---

## layout: default

## FdKit — Android Fast Development Kit

[Maven Central](https://central.sonatype.com/artifact/io.github.truegrom/bom)
Snapshot

Modular Android SDK with state, networking, logging, and slot-based Compose UI.

Example — declare the BOM once, then add only the modules you need:

```kotlin
dependencies {
    implementation(platform("io.github.truegrom:bom:<version>"))

    implementation("io.github.truegrom:utils")       // Result/Either/Value, coroutine helpers
    implementation("io.github.truegrom:state")       // StateViewModel, RemoteData, traits, errors
    implementation("io.github.truegrom:viewmodel")   // BaseViewModel (task/uniqueTask)
    implementation("io.github.truegrom:repository")  // BaseRepository, BaseDispatchers
    implementation("io.github.truegrom:logging")     // FdkLog, LogSink, Timber backend
    implementation("io.github.truegrom:http-error")  // HttpError hierarchy, HttpErrorMapper
    implementation("io.github.truegrom:network")     // Ktor HttpClient (@BaseHttp)
    implementation("io.github.truegrom:crypto")      // CryptoManager (Tink + Keystore)
    implementation("io.github.truegrom:datetime")    // java.time format extensions
    implementation("io.github.truegrom:ui-kit")      // Compose primitives, localized formatters
    implementation("io.github.truegrom:screen")      // FdKit* screen scaffolding
}
```

- [All artifacts on Maven Central](https://central.sonatype.com/namespace/io.github.truegrom)
- [BOM](https://central.sonatype.com/artifact/io.github.truegrom/bom)
- [Using FdKit — Agent Skill]({{ "/fdkit-agent-skill.html" | relative_url }}) — guide for AI coding agents



## Example — simple screen

Minimal slice: `RemoteData` in state → `StateViewModel` load → `Fetchable` on the screen.

```kotlin
data class User(
    val id: Id,
    val name: String,
) {
    @JvmInline value class Id(val value: Long)
}

data class UserState(
    override val remoteData: RemoteData<User> = RemoteData.loading(),
) : RemoteDataState<UserState, User> {
    override fun withRemoteData(remoteData: RemoteData<User>) = copy(remoteData = remoteData)
}

class UserStateBuilder(override val initial: UserState) :
    BaseStateBuilder<UserState>(),
    RemoteDataOps<UserState, User>

@HiltViewModel
class UserViewModel @Inject constructor(
    private val repository: UserRepository,
) : StateViewModel<UserState, UserStateBuilder>(
    MutableStateOwner { UserState() },
    ::UserStateBuilder,
), Errors by MutableErrorManager() {

    init { loadUser() }

    fun loadUser() = uniqueTask("loadUser") {
        state { loading() }
        runCatching {
            val user = repository.user()
            state { fetched(user) }
        } handledError { error -> // rethrows CancellationException instead of handling it
            state { failed(error) }
        }
    }
}

@Composable
fun UserScreen(onBack: () -> Unit) = ViewModelScreen<UserViewModel> {
    ErrorEffects()

    FdKitBaseScaffold(
        topBar = {
            FdKitTopBarTextTitle(
                title = stringResource(R.string.user_title),
                onNavigateBack = onBack,
            )
        },
    ) {
        viewModel.Fetchable<User, UserState> {
            Fetched { user ->
                FdKitScreenColumn {
                    Text(user.name)
                }
            }
            Loading {
                // Here’s your awesome loader.
            }
            Error {
                // Here’s your error stub.
            }
        }
    }
}
```

More patterns (errors, actions, pull-to-refresh, paging) are in the [agent skill]({{ "/fdkit-agent-skill.html" | relative_url }}).