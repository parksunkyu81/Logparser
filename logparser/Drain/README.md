# Drain

Drain은 로그 파싱의 대표적인 알고리즘 중 하나입니다. 스트리밍 및 적시에 로그를 구문 분석할 수 있습니다. 구문 분석 프로세스를 가속화하기 위해 Drain은 구문 분석을 위해 특별히 설계된 규칙을 인코딩하는 고정 깊이 구문 분석 트리(아래 그림 참조)를 사용합니다.

https://ws1.sinaimg.cn/large/006tKfTcgy1ftuhiqqmazj30r40k4wgw.jpg드레인의 파스 트리 구조

사용자 정의 도메인 지식에 따라 첫 번째 전처리 로그를 드레이닝합니다. 정규식. 둘째, Drain은 사전 처리된 로그 메시지와 함께 파스 트리의 루트 노드에서 시작됩니다. 파스 트리의 첫 번째 계층 노드는 로그 메시지 길이가 서로 다른 로그 그룹을 나타냅니다. 셋째, Drain은 첫 번째 레이어 노드에서 리프 노드로 트래버스합니다. Drain은 로그 메시지의 시작 위치에 있는 토큰으로 다음 내부 노드를 선택합니다. 그런 다음 Drain은 로그 메시지와 각 로그 그룹의 로그 이벤트 간의 유사도를 계산하여 로그 메시지를 기존 로그 그룹에 넣을지 여부를 결정합니다. 마지막으로 Drain은 로그 메시지와 로그 이벤트의 동일한 위치에 있는 토큰을 스캔하여 파서 트리를 업데이트합니다.

Drain은 스트리밍 및 적시에 로그를 구조화된 이벤트로 구문 분석할 수 있는 온라인 로그 파서입니다. 

로그 그룹 검색 프로세스를 안내하기 위해 고정 깊이의 구문 분석 트리를 사용하므로 매우 깊고 불균형한 트리 구성을 효과적으로 방지할 수 있습니다.

다음 문서에서 드레인에 대한 자세한 내용을 읽어보십시오.

+ Pinjia He, Jieming Zhu, Zibin Zheng, and Michael R. Lyu. [Drain: An Online Log Parsing Approach with Fixed Depth Tree](http://jiemingzhu.github.io/pub/pjhe_icws2017.pdf), *Proceedings of the 24th International Conference on Web Services (ICWS)*, 2017.

Researchers from IBM made an upgrade version of Drain in Python 3.6 with additional features: [https://github.com/IBM/Drain3](https://github.com/IBM/Drain3)
