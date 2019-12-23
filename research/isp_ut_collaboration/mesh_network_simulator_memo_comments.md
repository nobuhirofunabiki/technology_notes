# Mesh Network Simulator コード読み解きメモ

- 2019/12/22 船曳敦漠
- 2019/12/23 清水 追記 : 追記箇所を"(S)"で表しています

## TODO list
- batmanの仕様を勉強する

## `main.py`
- `ArgumentParser`で`nwsim.toml`、`node_positions_simple.csv`を読み込む
    - (S) ArgumentParserでは、default値としてファイルを読み込むPathを設定していて、読込み処理そのものは別の場所で行っています。
        - (S) 具体的には、nwsim.tomlは、NWSimConfigで、node_positions_simple.csvは、SpaceTimeで読み込んでいます。
- `ArgumentParser`で読み込んだ情報を引数として`NetworkSimulator`のコンストラクタに渡す
    - `nw_sim = NetworkSimulator(args)`
- `nw_sim.run()`: シミュレーション実行

## `network_simulator.py`
- `NetworkSimulator`クラスの実装
- `run(self)`: mesh_network_simulatorの核となるラッパーメソッド
    - `nodes_trip_times`リストにこのシミュレータの出力となる通信時間を収納
    - `_create_substantial_model(self)`
        - `MeshNodes`クラス、`MeshEdges`クラスの実体がこのメソッド内で生成される
    - `for space in self.space_time`: `node_positions_simple.csv`から読み込んだ時間リストを使ってイタレーション
    - `_build_mesh_network(space)`:
        - その時刻の衛星位置情報に応じて、ネットワークを切り替える
        - `SpaceTime`クラスの`__next__`メソッド内で`MeshGraph`クラスが実体化され、`MeshGraph`のコンストラクタで衛星間距離を計算する(`self.dist = self._calc_distance()`)
        - `MeshGraph`から得られるネットワーク接続状態をもとに、docker networksを更新する
            - `self.connectivity_dict[k] = v['connectivity']`
            - `MeshEdge.connect(bridge, node_pair)` または `MeshEdge.disconnect(bridge, node_pair)`
    - `_measure_trip_time(space)`:
        - `_build_mesh_network`メソッドで更新されたネットワーク上での通信時間を計算する
        - `MeshNode`クラスの実体リストを一つずつ確認
            - ハブノードかその他のノードかに応じて処理を変更
        - `result_lines = node.exec_run("batctl", "ping", "-c", "3", "-R", "-i", f"{INTERNAL}", hub_node_mac)`
            - pingを飛ばして通信時間を計測

## `nwsim_config.py`
- `NWSimConfig`クラスの実装
- `NetworkSimulator`のコンフィグ情報を管理するためのクラス

## `space_time.py`
- `SpaceTime`クラスの実装
- `node_positions_file`からノード数、時間リストを読み込み

## `mesh_node.py`
- `MeshNode`クラスの実装
- コンテナを管理
- `nodes = client.containers.list()`

## `mesh_edge.py`
- `MeshEdge`クラスの実装
- ネットワークを管理
- `edges = client.networks.list()`

## `mesh_graph.py`
- `MeshGraph`クラスの実装
- ノード間の距離情報をもとに、ネットワークの接続状態を管理する
- `SpaceTime`の__next__メソッド内で実体ができる
    - `for k, v in space.mg.graph.edges.items():`