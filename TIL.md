Retrofit2
---------------

안드로이드에서 HTTP통신을 하기 위해서는 웹서버와의 통신을 위한 HttpUrlConnection, 메인쓰레드에서는 네트워크 작업을 할 수 없어 추가적으로 AsyncTack가 필요.

안전한 타입 방식의 HTTP 클라이언트이므로 URL 생성이나 매개 변수의 설정 등을 걱정할 필요 없이 네트워크로 보낼 쿼리 문법만 살펴보면 됩니다.
- Gradle에 추가
<p>
<code>compile 'com.squareup.retrofit2:retrofit:2.4.0'</code>
<code>compile 'com.squareup.retrofit2:converter-gson:2.4.0' // Retrofit2와 json 파싱을 위해 추가
</code>
</p>
- Interface 생성
<pre><code> public interface GitHubService {
  @GET("users/{user}/repos")
  Call<List<Repo>> listRepos(@Path("user") String user);
}</code></pre>
- Retrofit class 생성
> Retrofit class는 일반적으로 GitHubService Interface를 implementation함
<pre><code>Retrofit retrofit = new Retrofit.Builder()
    .baseUrl("https://api.github.com/")
    .build();
    GitHubService service = retrofit.create(GitHubService.class);</pre></code>
