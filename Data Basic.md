# @State, @Binding

### @ (Property Wrapper)

- 프로퍼티가 저장되는 방식을 관리하는 코드 추가 (재사용 가능)

### @State

- 변수의 값이 바뀔 때 해당 변수를 사용하는 View변수에서도 update가 이뤄지길 원할 때 사용
- 상태가 변하는 View를 만들 때 무조건 사용하게 됨

```swift
@State var backgroundColor = .blue
```

SwiftUI에서 `@State`는 상태 변화를 추적하고 해당 상태를 사용하는 View가 업데이트되도록 하는 데 사용되는 속성 래퍼입니다.

일반적으로 `@State`는 변수의 값이 변경될 때 해당 변수를 사용하는 View에서 업데이트가 이루어지길 원할 때 사용됩니다. 예를 들어, `@State`를 사용하여 배경색이나 텍스트의 변경과 같은 사용자 인터페이스 요소를 다룰 수 있습니다.

`@State` 속성은 해당 View 내에서만 사용할 수 있으며, View가 업데이트될 때마다 해당 속성에 대한 변경 사항을 감지하고 다시 그려집니다.

위의 예시에서 `backgroundColor`는 `@State` 속성으로 선언되었습니다. 이렇게 선언하면 `backgroundColor`의 값이 변경될 때마다 해당 View가 자동으로 다시 그려집니다.



## @Binding

- @State를 Subview에서 사용하기 위한 Wrapper

`@Binding`은 SwiftUI에서 사용되는 프로퍼티 래퍼입니다. 이 래퍼는 상위 뷰에서 하위 뷰로 데이터를 전달하기 위해 사용됩니다.

일반적으로, `@State`는 상위 뷰에서 정의되고 하위 뷰에서 사용될 때 사용됩니다. 하지만 `@State` 프로퍼티는 자신의 뷰 내에서만 사용할 수 있습니다. 하지만 `@Binding`을 사용하면 `@State` 데이터를 하위 뷰로 전달하여 하위 뷰에서 해당 데이터를 업데이트할 수 있습니다.

`@Binding`을 사용하기 위해서는 다음과 같은 단계를 따라야 합니다:

1. 상위 뷰에서 `@State` 프로퍼티를 정의합니다.
2. 하위 뷰에서 해당 `@State` 프로퍼티를 `@Binding`으로 사용합니다.
3. 하위 뷰에서 `@Binding`을 통해 데이터를 읽거나 업데이트합니다.

예를 들어, 다음과 같이 사용할 수 있습니다:

```swift
struct ContentView: View {
    @State var backgroundColor = Color.blue

    var body: some View {
        VStack {
                        // parameter로 사용할 @State 프로퍼티 값에 $를 붙인다
            ColorPicker("Background Color", selection: $backgroundColor)
            Subview(backgroundColor: $backgroundColor)
        }
    }
}

struct Subview: View {
    @Binding var backgroundColor: Color

    var body: some View {
        Rectangle()
            .foregroundColor(backgroundColor)
            .frame(width: 200, height: 200)
    }
}

```

이 예시에서, `ContentView`에서 `@State`로 `backgroundColor`을 정의하고, `Subview`에서 `@Binding`으로 동일한 `backgroundColor`을 사용합니다. 이로써 `Subview`에서 `backgroundColor`을 업데이트하면 해당 변경 사항이 `ContentView`에도 반영됩니다.

이렇게 `@Binding`을 사용하면 상위 뷰와 하위 뷰 간의 데이터 흐름을 쉽게 관리할 수 있습니다.


# ExtractView

- body의 code가 길어지는 경우 View를 컴포넌트 화 (method 또는 property로 분리할 수 있다)
    - body 내부가 간단해지고, subView 별로 코드를 찢어놓는 경우 가독성이 좋아짐
- code가 여러번 반복되는 경우 View를 아예 다른 파일로 분리하는 것도 good
