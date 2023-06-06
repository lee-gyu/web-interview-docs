# 추상화 (Abstraction)

> 우리는 깊게 생각하지 않는다. 우리는 추상화한다.

S/W 세계의 다양한 개념들은 추상화를 통해 표현된다.\
더 자세히 알면 알수록, 더 깊게 들어가면 들어갈수록, 더 많은 것을 알아야 한다.\
내부 동작 원리를 아는 것은 매우 중요하다, 하지만 많은 공부 시간을 필요로 한다.\
시간은 한정되어져 있고, 회사는 빠른 결과물을 원한다.

추상화를 통해 우리는 손쉽게 컴퓨터를 사용한다.\
사용자는 UI를 통해 쉽게 컴퓨터 자원을 사용하며, 필요한 작업을 수행한다.\
만약, 추상화가 되어 있지 않더라면, 사용자는 모든걸 주의 깊게 알아야 한다.\
컴퓨터의 동작 원리며, 프로그래밍 언어의 문법, 프로그램의 동작 원리 등을 알아야 한다.

모든 것을 다 알기에는 힘들다.\
그러기에는 우리 인간 사회는 전문 분야마다 분업화가 쭉 되어져 왔다.\
이를 통해 각자 전문적인 분야에 집중하여 일을 수행한다.\
이러한 분업화는 추상화를 통해 이루어진다.

PC의 전원버튼도 추상화 되어 있는 하나의 작업이다.\
전원버튼은 하드웨어에 전력을 공급하는 인터페이스이며,\
이를 통해 부팅이라는 작업을 수행한다.\
부팅이라는 작업은 부트로더가 수행하며, 부트로더는 BIOS가 수행한다.\
이를 통해 보조 저장장치에 저장된 OS를 메모리에 로드하고, 실행하며, 컴퓨터가 실행된다.

이 모든 과정을 사용자는 알 필요가 없다.\
"컴퓨터 전원 버튼을 눌러 컴퓨터를 작동시킨다." 이것으로 추상화되어 있다고 볼 수 있다.

PC 작업을 떠나 우리가 사용하는 소프트웨어 API는 어떠한가?\
API도 응용 프로그램이 원하는 작업을 수행해주는 하나의 추상화된 정의에 불과하다.\
API 속에서 내부적으로 어떻게 동작하는지 알 필요가 없다.\
물론 시스템적 결함이 발생하면 알아야한다. API가 어떤 흐름으로 어떤 자원을 사용하는지.\

추상화를 통해 우리는 생산성을 확보할 수 있고,\
각자의 직업에 따른 분업화를 이룰 수 있는 것이라 생각된다.