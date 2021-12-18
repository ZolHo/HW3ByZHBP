PS：多人联机不能重名，Windows Only

完成内容：

- 动画：联机模式下的带瞄准偏移，混合空间，姿势混合的人物动画
- 联机：带有联机大厅的，聆听服务器模式的局域网联机游戏。大厅内，可同步准备状态，房主开始游戏。游戏内玩家可重生，记录KDA，同步开局和结束，结算获胜玩家。地图中会自动补充枪支，血包和弹药并同步。
- 人机：人机可使用武器攻击玩家，发现但攻击不到玩家时会追踪玩家，血量不足时会寻找最近的血包回血，且人机可配置不同的血量和武器。玩家可以攻击人机，消灭地图中所有的人机后获胜。
- 游戏内重要蓝图：
  - AutoSpawnActorNew：可自动生成actor，并在该acotr销毁时重新生成。可配置生成的actor类型及重新生成的间隔时间。生成的actor需要实现CanBePickUp接口，就可实现玩家拾取后自动生成新的actor。
  - BaseGun：枪的基类，抽象类，实现了枪支的功能，玩家pawn可在不知道枪的具体类型的情况下使用其子类。其子类通过构造函数配置属性及模型来产生不同手感的枪，也可以通过重载来实现更个性化的配置。
  - RobHat地图的GameMode（GM），PlayerController（PC），Character，分工合作完成了联机模式，缺点是三者之间稍微有些耦合，character中不应该引用具体的PC，PC也不应该太依赖GM。所以复用到单机模式时没办法很好的适配。且因为刚开始学联机，应该很多地方产生了不必要的网络同步。（本来是想做一个RobHat抢帽子的游戏，但是精力有限，只做成了单纯的杀人数最多者胜）
- 其他：各种界面，受击提醒，击中反馈等

