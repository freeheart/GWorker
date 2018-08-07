//-------------Auto kill the NPC in the map
var WorkToName="弟子"
var auto_work=function(){
	let battle_status=RoleProxy.getInstance();
	let b=battle_status.facade.view.mediatorMap.BattleSceneMediator;
	if(b.isPopUp==false){
		let isfind=0;
		for(let i=0;i<RoomProxy.getInstance().roomNpcList.length;i++){  //find npc and do
		if( RoomProxy.getInstance().roomNpcList[i].name.match(WorkToName) &&
				RoomProxy.getInstance().roomNpcList[i].state == 1){
				netProtocol.C2S_BATTLE_KILL.sendMsg(1, RoomProxy.getInstance().roomNpcList[i].npcId, 1)
				break;
			}
		}
	}
	for(let i=0;i<RoomProxy.getInstance().roomNpcList.length;i++){
		if(RoomProxy.getInstance().roomNpcList[i].state==2){
			netProtocol.C2S_NPC_PICK_UP.sendMsg(RoomProxy.getInstance().roomNpcList[i].npcId)
		}
	}
}
var Auto_Work_Robot=window.setInterval(auto_work,100)

//-------------auto fight ,add blood , close winpage
var AI_fight=function(){
	let battle_status=RoleProxy.getInstance();
	let b=battle_status.facade.view.mediatorMap.BattleSceneMediator;
	if(b.NowQi>=4 && b.isPopUp ==true ){  //auto do sth.
	let i = new ceshipackage.C2SBattleSkillCast,j=new ceshipackage.C2SBattleSkillCast;
		i.skillId = 256;j.skillId = 263;
		i.cardPlace =11;j.cardPlace =31;
		i.comboId =2;j.comboId =2;
		let o = new egret.ByteArray(ceshipackage.C2SBattleSkillCast.encode(i).finish());
		SocketManager.getInstance().sendMessage(C2SCommandEnum.C2S_BATTLE_SKILL_CAST, o);
		let o2 = new egret.ByteArray(ceshipackage.C2SBattleSkillCast.encode(j).finish());
		SocketManager.getInstance().sendMessage(C2SCommandEnum.C2S_BATTLE_SKILL_CAST, o2);
	}
	if(b.isPopUp ==true){
		if(b.BattlefieldScenePanle.getChildByName("layer_1000") == null){
			b.closeBattleScene();
		}
	}
	if(RoleProxy.getInstance()._roleBaseInfo.roleBattleAttrMap[34] <
		RoleProxy.getInstance()._roleBaseInfo.roleBattleAttrMap[12]){  //heal up
		netProtocol.C2S_HEAL.sendMsg();
	}
}
var AI_fight_Robot=window.setInterval(AI_fight,100)
