# AsyncMoya


1. Extension MoyaProvider

```
import Moya

extension MoyaProvider {
    func request(_ target: Target, callbackQueue: DispatchQueue? = .none, progress: Moya.ProgressBlock? = .none ) async -> Result<Response, MoyaError> {
        return await withCheckedContinuation { continuation in
            self.request(target, callbackQueue: callbackQueue, progress: progress) { result in
                continuation.resume(returning: result)
            }
        }
    }
}

```



2. Use

```
let response =  await provider.request(.testRequest)

```

