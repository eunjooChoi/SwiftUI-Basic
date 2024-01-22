# MVVM

## Model:

- 앱의 데이터와 비즈니스 로직을 캡슐화. 뷰와 독립적

## View:

- UI 정의

## ViewModel:

- View에 데이터 제공, Model에 업데이트 요청
    
    ### @ObservedObject VS @StateObject
    
    - ObservedObject
        - 객체화를 만들어서 내부에 일어나는 변화를 기반으로 어떻게 화면을 다시 그리는지 보여줌
        - 새로고침되면 일부 애니메이션이 있기 때문에 값이 새로고침이 됨
        - SubView에서 부모 뷰의 viewmodel을 사용할 때 사용
    - StateObject
        - 하나의 객체로 만들어지고, View가 얼마나 초기화 되는지 상관 없이 별개의 객체 관리
        - View와 별개의 메모리 공간에 저장해 데이터를 안전하게 보관
        - 뷰를 처음 초기화 할 때 사용
    
    ### EnvirnmontObject
    
    - 앱의 많은 뷰와 데이터를 공유해야 할 때 사용
