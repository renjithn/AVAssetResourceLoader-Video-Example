# AVAssetResourceLoader-Video-Example
Implementation of AVAssetResourceLoader custom class which can be useful while caching cideos while streaming

Usage

AVURLAsset *asset ;
assetLoader = [[AssetLoaderDelegate alloc] init];
assetLoader.fileUrl = self.compilation.VideoUrl;
asset = [AVURLAsset URLAssetWithURL:[self url:[NSURL URLWithString:urlString] WithCustomScheme:@"streaming"] options:nil];
[asset.resourceLoader setDelegate:assetLoader queue:dispatch_get_main_queue()];


- (NSURL *) url:(NSURL*) url WithCustomScheme:(NSString *)scheme{
    NSURLComponents *components = [[NSURLComponents alloc] initWithURL:url resolvingAgainstBaseURL:NO];
    components.scheme = scheme;
    return [components URL];
}
