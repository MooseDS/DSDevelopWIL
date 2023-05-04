# FLOW

## TIL-230503
## 잘한점
- 단일 Suspend fun 실행을 통한 UiState 초기화가 아닌 여러개 Suspend fun 으로 부터 필요 변수를 불러올때 방법이 필요했다. UiState - Loading 변수를 활용하여 Ui 에서 결과 값을 기다리며 변수 초기화 결과값을 기다린 후 업데이트 할 수 있도록 함.

<pre><code>
  private val _state: MutableStateFlow<UiState> = MutableStateFlow(UiState(isLoading = true))

  init {
    viewModelScope.launch {
        val result1 = suspendFunction1();
        val result2 = suspendFunction2();

        _state.update {
            result1.aa,
            result2.bb,
         }
    }
  }
</code></pre>

## 배운점
- [Migrating from LiveData to Kotlin flow](https://medium.com/androiddevelopers/migrating-from-livedata-to-kotlins-flow-379292f419fb) 을 통해 자주사용되는 패턴을 활용하려고 고민하다보니 해결점을 쉽게 찾을 수 있었다.


------------
## TIL-230503
## 잘한점
- UiState EditText 초기값과 이벤트가 발생했을 때의 값과 같은지를 확인 할 수 있는 방법은 ViewModel 에서 초기값을 변수로 저장하고 있는다.

<pre><code>
   private val _state: MutableStateFlow<UiState> = MutableStateFlow(UiState()) 

    private lateinit var firstTextValue: String
</code></pre>

## 배운점
- Flow로 무조건 해결해야 해보겠다는 강박에 ViewModel이 아닌 Repository 에서 값을 저장하고 있어야 한다 생각했다.

> Flow, Suspend Function의 Return 값을 flow로 만들수 있는가 ?

- 둘의 차이점은 결과값을 한번 전달할 것인지 지속적으로 해야하는지가 중요!!
