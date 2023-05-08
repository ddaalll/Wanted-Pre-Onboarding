# Wanted-Pre-Onboarding

객체지향 생활 체조

1. 한 메서드에 오직 한 단계의 들여쓰기만 합니다.
2. else 표현을 사용하지 않습니다

func abc() {
    
    if 1 < 2 {
        
    }
    
}

3. 모든 원시 값과 문자열을 포장합니다.

enum Lotto {
    
    static let numberRange = (1...45)
    
    static let lotteryCount = 6
    
    enum Message {
        
        static let wrongPicks: String = "선택이 잘못되었습니다."
        
        static let win: String = "축하합니다"
        
    }
    
}

func makeLottoNumbers() -> [Int] {
    
    var numbers: Set<Int> = []
    
    while numbers.count <  Lotto.lotteryCount,
          
            let random: Int = Lotto.numberRange.randomElement() {
        
        numbers.insert(random)
        
//        randomElement() {

//            numbers.insert(random)

        }
        
        return Array(numbers)
        
    }
}
4. 한 줄에 점을 하나만 사용합니다.

    디미터 법칙

    -디미터 법칙은 모듈은 자신이 조작하는 인스턴스의 속사정을 몰라야 한다는 법칙입니다.

    -인스턴스는 자료를 숨기고 메서드를 공개합니다. 즉, 인스턴스는 조회 메서드로 내부 구조를 공개하면 안됩니다.

    -다음 코드는 디미터 법칙을 어기는 것으로 볼 수 있습니다.

let output: String = text.options().scratch().absolutePath()


5. 이름을 줄여 쓰지 않습니다(축약 금지)
6. 모든 엔티티를 작게 유지합니다. // 함수(메서드), 타입을 작게 쪼개보세요
7. 3개 이상의 스위프트 기본 데이터타입(Int,String,Double 등) 프로퍼티를 가진 타입을 구현하지 않습니다.
struct Animal {
    struct PhysicalInfo {
        var weight: Double
        var height: Double
        var numberOfLegs: Int
    }
    
    struct BioInfo {
        enum Gender {
            case male
            case Female
            case unknown
        }
        struct Age {
            var value: Int
            
            init?(value: Int) {
                let commonAgeRange = (0...300)
                guard commonAgeRange.contains(value) else { return nil }
                self.value = value
            }
        }
    }
}
8. 일급 콜렉션을 사용합니다
 단 하나의 컬렉션만 프로퍼티로 가지는 타입

class Stack<Item> {
    private var items: [Item] = []
    func push(_ item: Item) {
        items.append(item)
    }
    
    func pop() -> Item {
        return items.removeLast()
    }
}

var intStack = Stack<Int>()
intStack.push(3)

9. getter/setter를 구현하지 않습니다.
객체에게 일을 시키세요. 물어보지 말고.
프로퍼티의 값을 직접 빼오거나 직접 셋팅하지 않도록 해주세요(캡슐화)

class Person {
    var money: Double = 0
    
}

let yagom: Person = Person()
yagom.money = 10000
yagom.money = 0
print(yagom.money)

class Person1 {
    private var money: Double = 0
    
    func showMoney() {
        print("나 돈 이만큼 이찌롱 : \(money)")
    }
    
    func giveMoney(_ amount: Double) {
        money += amount
    }
}



SOLID 객체지향 프로그래밍을 위한 5가지 원칙, 내 코드에 적용했을때 어떤점이 개선되었거나 어떠했는가?
SOLID를 왜 지켜야 하는가? -높은 코드 품질을 얻기 위해서, 높은 품질의 코드는 무엇?

가치는 원칙보다 높은 수준의 개념

가치 > 원칙

원칙은 가치를 지키기위해서 존재해야한다.

소프트웨어의 가치

1. 가독성, 커뮤니케이션

-개발자는 코드를 통한 커뮤니케이션

-읽고 이해할 수 없는 코드가 더욱 가치가 없다

2.  단순성

-코드는 단순해야한다

-커뮤니케이션에 도움이 된다

-버그가 생길 틈이 없어짐

-미래의 확장을 위한 복잡한 패턴은 경계의 대상

3. 유연성

-기존의 코드를 수정하는 데에 많은 시간을 소비함

-유연성과 단순성은 trade off

유연성은 언제 챙겨? / 언제 부터 고민해? / Trade Off

처음엔 단순하게! → 기획 또는 정책의 변경이 발생 → 이 기획 또는 정책의 변경의 원인은 무엇일까? 그리고 이러한 변경은 계속 발생 가능한 일일까? → 리팩토링을 통해 확장성을 고려해서 변경해보자

왜 저 3가지가 중요한 가치일까?

가치는 도대체 어떤 기준으로 매긴걸까?

Cost VS Benefit

소프트웨어 세상에서 비용이란? 

주된 비용은 개발자들의 시간(연봉)

소프트웨어의 가치

1. 가독성, 커뮤니케이션
2. 단순성
3. 유연성

SOLID 원칙을 지켜야 하는 이유

## ⭐️기업에 생산성을 줄수 있고, 기업의 생산성은 기업의 베네핏을 올려 준다⭐️


API → 누군가가 호출한다
