# Text
## Methods
- .font(.title) : 해상도에 맞춰 responsive
- .font(.sytem(size:weight:design:) : 크기 직접 지정.
- .multilineTextAligning : 여러 줄로 되어 있는 텍스트 정렬 방법
- .fontWeight() : 두께 조정
- .italic() : 기울임
- .strikethrough(bool, color:) : 취소선
- .underline(bool, color:) : 밑줄
- .forgroundColor() : 글자 색 지정

# Shpae
## 기본적으로 지원해주는 다양한 shape 존재
- Circle
- Ellipse
- Capsule
- Rectangle
- RoundedRectangle

## Methods
- .fill(): 채우기
- .stroke(color, lineWidth:) 외곽선 세팅
- .trim(from: to:) : 도형을 자를 수 있음
- .frame(width: height: alignment:): 원하는 사이즈 지정

# Color
## 시스템 색 설정
- `.fill(.pink)`와 같이 시스템에서 제공하는 색 설정
- UIColor 사용: `.fill(Color(UIColor.secondarySystemBackground))`

## Hex Code Color
- 디테일한 컬러를 지정
- Assets에서 Color Set을 미리 지정한 뒤에 사용할 수 있다. (default/ dark 두 가지를 동시에 지정할 수 있음)
    - `.fill(Color("ColorSet지정이름"))`

## Dark Mode Color
- `.fill(.primary)` or `.fill(.secondary)`를 사용해보면 다크모드일 때 자동으로 색이 변하는 걸 확인 가능
    - Preview 코드에서 `.preferredColorScheme(.dark)` 사용하거나 프리뷰 화면에서 직접 조정해 다크모드일 때 컬러 확인 가능

## Gradient
- Linear Gradient
    - 선형으로 그라디언트 들어감
    
    ```swift
    .fill(
             LinearGradient(gradient: Gradient(colors: [Color.red, Color.blue]),
             startPoint: .leading,
             endPoint: .trailing)
          )
    ```
    

- Radial Gradient
    - 원하는 뱡향, 원형으로 그라디언트 들어감
    
    ```swift
    .fill(
             RadialGradient(gradient: Gradient(colors: [.yellow, .purple]),
                            center: .bottom,
                            startRadius: 5,
                            endRadius: 300)
          )
    ```
    

- Angular Gradient
    - 원하는 각도로 그라디언트 들어감

# Image
## SystemIcon
### SF Symbols

- Apple에서 제공하는 기본 아이콘들
    - `Image(systemName:)` 으로 호출

## ImageSet에 추가
- Assets 파일에 이미지를 직접 추가
    - `Image(”Asset Name”)`으로 호출

## Methods
- resizable() : 이미지 사이즈를 조절할 수 있게 함
- renderingMode()
    - renderingMode(.original)은 multi color로 변경. 고유값 컬러로 변경되어 color 변경이 안됨.
- scaleToFill()
    - 주어진 공간을 최대한 채움 (이미지 잘려도 상관 안함)
- scaleToFit()
    - 주어진 공간에 사진이 전부 나오도록 이미지 사이즈가 조절됨

# Frame
## Frame
- UI가 차지하는 사이즈를 정해줄 수 있다.
- height, width를 직접 지정할 수 있고, alignment를 설정할 수 있다
- maxWidth, maxHeight와 같이 최대 길이를 지정할 수 있다 (.infinity … )
- 마찬가지로 minWidth, minHeight로 최소 길이를 지정할 수 있다
- .background(): 컬러 조정

## Background
- 내가 원하는 프레임 뒤쪽에서 작업

## Overlay
- 내가 원하는 프레임 앞쪽에서 작업

```swift
             Image(systemName: "heart.fill")
                .font(.system(size: 40)) // Image인데 이걸로 크기 조정이 왜 되지?
                .foregroundStyle(.white)
                .background(
                    Circle()
                        .fill(
                            LinearGradient(gradient: Gradient(colors: [Color.red, Color.blue]), startPoint: .leading, endPoint: .trailing)
                        )
                        .frame(width: 100, height: 100)
                        .overlay(
                            Circle()
                                .fill(.red)
                                .frame(width: 35, height: 35)
                                .overlay(
                                    Text("3")
                                        .font(.headline)
                                        .foregroundStyle(.white)
                                )
                            , alignment: .bottomTrailing
                        )
                )
```
