---
title: "Deeplearning4j란?"
layout: kr-default
---

# Deeplearning4j란?

Deeplearning4j는 자바(Java)와 스칼라(Scala)를 위해 작성된 세계 최초의 상용 수준 오픈소스 심층학습(딥러닝) 라이브러리입니다. 연구 목적으로 쓰여진 다른 라이브러리와 달리, Deeplearning4j는 상용 서비스를 위해 설계되었고 하둡(Hadoop)/스파크(Spark)와 통합해 사용할 수 있습니다. 스카이마인드([Skymind](http://skymind.io))는 Deeplearning4j의 유료 사용자를 지원하는 회사입니다.

Deeplearning4j는 최신 기술을 간편하게 사용하는 데 초점을 두었습니다. 특히, 설치와 활용에 있어서 일반적인 문법과 규칙을 사용하였기 때문에 머신 러닝에 대한 깊은 지식이 없는 사람도 빠르게 시제품을 만들 수 있도록 하고 있습니다. 확장성에도 초점을 두어 어떠한 규모의 데이타에도 사용할 수 있습니다. Deeplearning4j는 아파치 2.0 라이센스로 배포되기 때문에 파생된 모든 소스 코드는 저작권이 코드의 작성자에게 귀속됩니다.

지금 바로 Deeplearning4j 예제 코드를 실행해 보세요. [빠른 설치 페이지의 안내](kr/kr-quickstart)를 따르면 인공 신경망 예제를 실행할 수 있습니다.

### [심층 학습 활용 사례](kr/kr-use_cases)

* 얼굴/이미지 인식
* 음성 검색
* 음성 인식 및 음성-문자 변환
* 스팸 메일 필터링 (비정상 행위 탐지)
* 전자 상거래 사기 탐지
* 추천 시스템 (고객관리, 고객 유지, 광고 기술)
* [회귀 분석](linear-regression)

### DL4J의 강점

* 다목적 N차원 배열 클래스([n-dimensional array class](http://nd4j.org/kr-index))
* [GPU](http://nd4j.org/gpu_native_backends.html) 통합
* [하둡](https://github.com/deeplearning4j/deeplearning4j/tree/master/deeplearning4j-scaleout/hadoop-yarn) 및 [스파크](spark)로 쉽게 확장 가능
* [카노바(Canova)](canova): 기계 학습을 위한 벡터 처리 기술
* [ND4J: Numpy의 두 배 속도를 자랑하는 선형 대수 라이브러리](http://nd4j.org/benchmarking)

Deeplearning4j는 분산 처리와 단일 스레드 처리를 모두 지원합니다. 분산 시스템에서 학습하는 경우 동시에 여러 서버 클러스터에서 학습을 진행할 수 있으며, 결과적으로 대량의 데이터를 신속하게 처리할 수 있습니다.
인공 신경망은 [Iterative Reduce (반복적인 리듀스 작업)](iterativereduce)를 통해 병렬로 학습되는데, 이 학습 작업은 자바, [스칼라](http://nd4j.org/scala.html) 및 [Clojure](https://github.com/wildermuthn/d4lj-iris-example-clj/blob/master/src/dl4j_clj_example/core.clj)와 모두 호환됩니다. 이렇게 오픈 스택에서 편하게 사용할 수 있도록 모듈화된 구조 덕분에 Deeplearning4j를 이용해 마이크로 서비스 아키텍처에 최초로 딥러닝 기술을 적용하고 있습니다.

### DL4J의 인공 신경망(Neural Networks)

* [RBMs: Restricted Boltzmann Machines](kr/kr-restrictedboltzmannmachine)
* [인공 신경망](kr/kr-neuralnet-overview)
* [자연어처리: Word2vec](kr/kr-word2vec)
* [컨볼루션 네트워크(CNNs, Convolutional Networks)](kr/kr-convolutionnets)
* 재귀 오토인코더([Recursive autoencoders](https://github.com/deeplearning4j/deeplearning4j/blob/master/deeplearning4j-core/src/main/java/org/deeplearning4j/nn/layers/feedforward/autoencoder/recursive/RecursiveAutoEncoder.java))
* [Deep-belief networks](deepbeliefnetwork)
* 딥 오토인코더([Deep autoencoders](http://deeplearning4j.org/deepautoencoder.html)) (자동 질의응답, 데이터 압축에 적용)
* 재귀 텐서 신경망(Recursive Neural Tensor Networks) (영상, 자연어 분석에 적용)
* 누적 디노이징 오토인코더([Stacked Denoising Autoencoders](http://deeplearning4j.org/stackeddenoisingautoencoder.html))
* 더 자세한 내용은 "[적절한 인공 신경망을 선택하는 방법](neuralnetworktable)"을 참고하십시오.


심층 신경망은 여러 가지 기계학습 작업에서 [최고의 정확도](accuracy)를 자랑합니다. 심층 신경망에 관한 자세한 소개는 [개요](kr/kr-neuralnet-overview) 페이지를 참고하세요. Deeplearning4j를 이용하면 여러 층을 조합하여 다양한 깊이와 종류의 인공 신경망을 쉽게 만들 수 있습니다 (층을 조합하는 방법에 따라 RBM, 오토 인코더, CNNs, RNNs 등을 구현할 수 있습니다). 또, 모든 인공 신경망은 CPU 혹은 GPU기반의 하둡/스파크로 분산 처리할 수 있습니다.

저희가 그동안 개발한 라이브러리와 그 적용 방법은 아래와 같습니다.

![Alt text](../img/schematic_overview.png)

심층 신경망을 설계/학습하는 과정에서 여러분은 수많은 매개변수를 지정해주어야 하는데, 이 매개변수는 주어진 문제와 상황에 따라 적합하게 설정되어야 합니다. 저희는 자바, [스칼라](https://github.com/deeplearning4j/nd4s) 및 [Clojure](https://github.com/whilo/clj-nd4j) 개발자들이 Deeplearning4j를 도구로써 편리하게 사용할 수 있도록 설계/학습과정에서 지원을 아끼지 않습니다.

간략한 질문이 있다면 [Gitter](https://gitter.im/deeplearning4j/deeplearning4j)를 이용해 주세요. 프리미엄 서비스를 원하시면 [Skymind](http://www.skymind.io/contact/)로 연락을 주시기 바랍니다.

[ND4J는 저희가 사용하는 자바 기반 연산 엔진입니다](http://nd4j.org/kr-index). 크기가 큰 행렬을 다루는 경우 벤치마크에서 [ND4J는 Numpy 대비 대략 두 배 가까이 빠른 연산성능](http://nd4j.org/benchmarking)을 보여줍니다.

![Alt text](../img/logos_8.png)
