# ShinevvSdkJS
北京亮眼云视科技有限公司

## Design goals
一个基于JavaScript，给web或微信小程序提供基础音视频能力的SDK

## Reference
```
<script src="https://vvroom.shinevv.cn/js/ShinevvSdk.js"></script>
```

## Demo
```
https://vvroom.shinevv.cn/dist/
```

### example
```
<video id="videoLocal" width="240" height="320" src="" autoplay></video>

<video id="video_remote" width="240" height="320" src="" autoplay></video>

const localMemberId = 'chenc100';

const displayName = '亮眼云';

const roomId = '10100';

const shinevv = new Shinevv(localMemberId, displayName, 'vvroom.shinevv.cn', 3443);

shinevv.joinRoom(
    roomId,
    true,
    function(){
	    console.log('joinRoom onSuccess');
      
      shinevv.setVideoLabel(localMemberId, 'videoLocal');
	},
    function(reason){
        console.log('joinRoom onFail reason = %s',reason);

        shinevv.leaveRoom();

        shinevv = null;
    },
    function(){
        console.log('joinRoom onDisconnected');
        
        shinevv.leaveRoom();

        shinevv = null;
    },
    function(reason){
        console.log('joinRoom onClose reason = %s', reason);

        shinevv.leaveRoom();

        shinevv = null;
    },
    function(remote_memberId, displayName){
        console.log('joinRoom onNewMemberJoined remote_memberId = %s, displayName = %s',remote_memberId, displayName);

        shinevv.setVideoLabel(remote_memberId,'video_remote');
    },
    function(remote_memberId, displayName){
        console.log('joinRoom onMemberLeft remote_memberId = %s, displayName = %s',remote_memberId, displayName);
    },
    function(memberId, kind, bOpen){
        console.log('joinRoom onMemberStatusChange memberId = %s, kind = %s bOpen = %s',memberId, displayName, bOpen.toString());
    });
```

### License
Shinevv©2018 Beijing Technology Co., Ltd. All rights reserved.