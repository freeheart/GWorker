# GWorker
A auto-worker for web-game
暂时用，那个叫“泪痕”的拿去用
运行用：
var iia=window.setInterval(function(){
	let battle_status=RoleProxy.getInstance();
	let b=battle_status.facade.view.mediatorMap.BattleSceneMediator;
	netProtocol.C2S_BATTLE_KILL.sendMsg(1, RoomProxy.getInstance().roomNpcList[0].npcId,3);
	if(b.isPopUp ==true){if(b.BattlefieldScenePanle.getChildByName("layer_1000") != null)b.closeBattleScene();}
},2000)

停下来用：
window.clearInterval(iia)
