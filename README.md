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
