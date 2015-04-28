# AVAssetResourceLoader-Video-Example
Implementation of AVAssetResourceLoader custom class which can be useful while caching videos while streaming

## Usage

```
AVURLAsset *asset ;
assetLoader = [[AssetLoaderDelegate alloc] init];
assetLoader.fileUrl = self.videoURL ; //S3 url in this case
asset = [AVURLAsset URLAssetWithURL:[self url:self.videoURL WithCustomScheme:@"streaming"] options:nil];
[asset.resourceLoader setDelegate:assetLoader queue:dispatch_get_main_queue()];


- (NSURL *) url:(NSURL*) url WithCustomScheme:(NSString *)scheme{
    NSURLComponents *components = [[NSURLComponents alloc] initWithURL:url resolvingAgainstBaseURL:NO];
    components.scheme = scheme;
    return [components URL];
}

```
