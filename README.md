# contextual-retrieval
이 Repository는 Anthropic의 Contextual retrieval에 대해서 구현한 내용을 소개하고 있습니다.

Anthropic의 [Contextual Retrieval](https://console.aws.amazon.com/rds/home)은 기존 RAG(Retrieval-Augmented Generation) 방식의 한계를 극복하기 위해 고안된 검색 개선 기술입니다. 전통적인 RAG는 문서를 작은 청크로 나누고 임베딩하지만, 이 과정에서 각 청크가 원래 문서의 맥락을 잃어버려 검색 정확도가 떨어지는 문제가 있었습니다.
Contextual Retrieval은 이 문제를 해결하기 위해 각 청크에 간결한 설명(문맥)을 추가한 뒤, 이를 임베딩하거나 BM25 인덱스를 생성하는 두 가지 핵심 기술을 사용합니다.

- Contextual Embeddings: 각 청크 앞에 해당 청크가 어떤 맥락에서 등장하는지 설명하는 텍스트(문맥)를 추가해 임베딩합니다.
- Contextual BM25: BM25와 같은 키워드 기반 검색에서도 이 문맥 정보를 반영해 인덱싱합니다.

이 과정은 Claude와 같은 LLM을 활용해 각 청크의 문맥 설명을 자동 생성하며, 이를 통해 검색 실패율을 49%까지 줄였고, reranking(재정렬)까지 결합하면 최대 67%까지 감소시킬 수 있음을 실험적으로 확인했습니다.
즉, Anthropic의 Contextual Retrieval은 청크별 문맥 정보를 추가함으로써 의미 기반 임베딩과 키워드 검색의 장점을 결합하고, 대규모 지식 베이스에서도 더 정확한 정보 검색을 가능하게 하는 최신 RAG 성능 향상 기법입니다.

Contextual Retrieval을 적용했을 경우에 검색 결과에 어떻게 영향을 미치는 지에 대해서 테스트를 수행하였습니다.
아래 동여상을 통해서 해당 내용을 확인해 볼 수 있습니다.

[Contextual Retrieval Test 동영상](https://byekang-share-materials.s3.ap-northeast-2.amazonaws.com/github-share-files/Demo_HOL_20241110.mp4)


