# Week13

### 진행상황

    박승준 - Xml문서를 파싱하는 방법으로 XmlPullParser를 사용했고, AsyncTask 클래스를 상속받아 에러를 방지해보았다.
            doInBackGround 단계에선 웹서버에서 웹문서를 가져와서 화면에 표시하도록 만들었고, 인증키(서비스키)를 적용하기 위해서 Get데이터 방식을 사용했다.
            버스번호가 입력시에 다운로드 실패가 뜨고 있어 문제를 해결하는 중에 있다.
    
    김다혜 - firebase를 연결해 출발장소, 도착장소, 탑승인원, 출발시간을 입력하면 정보가 저장되고, recyclerview를 통해 택시 모집글이 작성된다. 
            현재 모인 인원은 무조건 1명에서 시작되고, 한명이 클릭할때마다 1명씩 늘어나고 모인인원이 모집인원과 수가 같아지면 
            인원이 가득찼다는 메세지와 함께 더 이상 인원이 늘어나지 않는다.
    
    마혜준 - 회원가입을 하면 DB에 저장이 되나, 로그인이 되지 않고 있는 오류가 있었는데, 
            firebase authentication에서 다양한 종류의 회원정보를 저장할 수 없어서 그런 것 같아서 Realtime DB로 구현 중에 있다. 
            각자 맡은 부분을 합치고 merge할 때, 뒤섞이면서  gradle이랑 manifest부분에서 오류가 난 것 같다. 새로 만들어 구현을 하며, 왜 안되는지 비교 중에 있다.
    
    박윤빈 - 시간표, 강의 목록이 있던 메인 화면에 일정 관리 버튼을 추가해 일정을 관리할 수 있는 화면을 만들었다. 
            달력 형식으로 구현했고 기본으로는 현재 날짜가 뜨게 하고 달력에서 달을 선택해서 원하는 날짜를 지정해 할 일을 작성하고 저장할 수 있도록 만들었다. 
            강의 목록에서 강의를 불러오는 방식으로는 강의 DB를 php를 이용해 불러오도록 하고 있는데 강의 정보가 제대로 뜨지 않아서 이 부분을 집중적으로 할 생각이다.
    
    심우정 - 게시글 작성시간과 댓글 작성시간 모두 분으로만 계산이 되었었는데 simpleDateFormat를 이용해 작성 날짜까지 DB에 넣고 불러올 수 있게 했다. 
            게시글이나 댓글을 작성한지 1시간 이내는 분으로, 24시간 이내는 시간으로, 그 이후부터는 작성날짜가 나오도록 했다.
            또한 파이어베이스에 DB를 보낼 때 키값을 지정하지 않고 자동생성 키 값으로 저장하는 방식 push()을 사용했는데 한 눈에 알아보기 쉽도록 board_num을 이용해 
            1번글, 2번글… 이런식으로 생성되도록 child(“Board”).child(board_num+”번글”).setValue(boardInfo); 이런 식으로 수정해서 작성했다.
            또한 파이어베이스 Like 테이블 안에 있는 like_count, 즉 좋아요 개수에 따라 null과 0이면 좋아요 버튼이 안 눌려져있는 상태로, 
            1이상이면 좋아요 버튼이 이미 눌려져 있는 상태로 버튼을 비활성화/활성화 할 수 있게 했다.  
            그리고 각각 게시글마다 좋아요 버튼을 눌렀는지, 안 눌렀는지 게시글 num마다 다르게 만들었다.
            마지막으로 좋아요 클릭과 취소를 하면 orderByChild와 equalTo를 이용해 각 게시글의 like_count로 이동하고, 
            removeValue()를 통해 버튼을 누를 때마다 새로운 child가 생기는 게 아닌, like_count만 늘어났다 줄었다 할 수 있도록 만들었다.
            이제 사용자 id에 따라 어떤 게시글에 좋아요를 클릭했는지, 여러 사용자가 클릭하면 그만큼 like_count가 계속 늘어나고, 
            많은 좋아요를 받은 게시글을 뽑아 인기게시판을 만드는 것이 목표다.
    
    양하은 - 메인화면에 모두들의 화면을 추가하기위해 다듬는 작업을 했다. 
            메인화면에서 fragment에서 cardview를 연결하는 부분 등 fragment 밖에서는 잘되는 기능이 fragment 안으로 들어가면 오류가 나는 부분이 있어서 이것을 고쳐나가는 중이다.  
            채팅 부분에서는 영어로 안되는 부분을 해결하였다. 
            그러나 단체채팅에는 어려움이 있다고 생각하여 친구추가를 하면 친구와 채팅이 가능하도록 하기로 결정하였다. 그래서 친구추가 부분 담당이 완성하면 바로 연동할 예정이다.
            채팅 부분에서 그냥 흰 바탕에 글자만 올라가는 것이 아니라 채팅을 보내면 배경이 생기도록 layout을 꾸밀 예정이다.
            
## 실행 화면
##### 박승준(버스 정보)
<img src="https://user-images.githubusercontent.com/80022793/120227691-9bc85080-c284-11eb-995c-3ae3fbc7b8f1.png" width="300" height="300">

##### 김다혜(셔틀 버스, 택시 모임 구하기)
<img src="https://user-images.githubusercontent.com/80022793/120227721-ada9f380-c284-11eb-83a5-8d082ea3f191.png" width="300" height="420"><img src="https://user-images.githubusercontent.com/80022793/120227734-b39fd480-c284-11eb-9899-edd73e895e40.png" width="270" height="420"><img src="https://user-images.githubusercontent.com/80022793/120227744-b8fd1f00-c284-11eb-9689-1896981dab1f.png" width="450" height="300">

##### 마혜준(회원가입, 로그인)
<img src="https://user-images.githubusercontent.com/80022793/120228535-48570200-c286-11eb-926e-a41aeed45b22.png" width="240" height="400"><img src="https://user-images.githubusercontent.com/80022793/120228543-4bea8900-c286-11eb-81b2-53249df06c23.png" width="240" height="400">
![image](https://user-images.githubusercontent.com/80022793/120228525-412ff400-c286-11eb-957d-616ecb839532.png)

##### 박윤빈(시간표, 일정)
<img src="https://user-images.githubusercontent.com/80022793/120229169-86085a80-c287-11eb-848c-5ac536ecc361.png" width="240" height="380"><img src="https://user-images.githubusercontent.com/80022793/120229181-8bfe3b80-c287-11eb-8ee4-5f77e19a0fd2.png" width="240" height="380"><img src="https://user-images.githubusercontent.com/80022793/120229200-93254980-c287-11eb-9136-899a4ab04217.png" width="240" height="380">

##### 심우정(게시판)
<img src="https://user-images.githubusercontent.com/80022793/120229471-2d858d00-c288-11eb-9896-5d05d7a7ab46.png" width="450" height="270"><img src="https://user-images.githubusercontent.com/80022793/120229483-324a4100-c288-11eb-90db-36d7a283c8f7.png" width="450" height="270"><img src="https://user-images.githubusercontent.com/80022793/120229491-36765e80-c288-11eb-8c71-eaebe8c3df50.png" width="450" height="270"><img src="https://user-images.githubusercontent.com/80022793/120229498-3aa27c00-c288-11eb-822e-dd713daeb49f.png" width="450" height="270">

##### 양하은(메인화면, 채팅, (졸업학점 계산))

<img src="https://user-images.githubusercontent.com/80022793/120323629-a6d0be80-c320-11eb-83f1-76a9055bc25c.png" width="400" height="400"><img src="https://user-images.githubusercontent.com/80022793/120311573-9dd8f080-c312-11eb-86bb-6254b6530713.png" width="450" height="270">
<img src="https://user-images.githubusercontent.com/80022793/120324213-560d9580-c321-11eb-8803-a0c34e953ad6.png" width="220" height="380"><img src="https://user-images.githubusercontent.com/80022793/120324378-848b7080-c321-11eb-91a6-402ac6485bea.png" width="220" height="380">
            
## Project Milestone
![image](https://user-images.githubusercontent.com/80022793/120225254-dbd90480-c27f-11eb-8522-821f5722b238.png)
![image](https://user-images.githubusercontent.com/80022793/120225400-1e024600-c280-11eb-9889-55edd0bb2a7f.png)
![image](https://user-images.githubusercontent.com/80022793/120225450-3d996e80-c280-11eb-9e16-b458edc0adb3.png)
