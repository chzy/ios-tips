## MJRefreash的使用


## 1:安装：

````
cocoapods导入：pod 'MJRefresh'
手动导入：
将MJRefresh文件夹中的所有文件拽入项目中
导入主头文件：#import "MJRefresh.h"
````

## 2：基本使用

````objc

- (void)configMJRefresh{

	//配置上拉刷新和加载控件
    [self.table addHeaderWithTarget:self action:@selector(headerRereshing)];
    [self.table addFooterWithTarget:self action:@selector(footerRereshing)];
    //设置加载的文字
    self.table.headerRefreshingText = @"玩命加载中";
    self.table.headerPullToRefreshText = @"下拉开始刷新";
    self.table.headerReleaseToRefreshText = @"松开开始刷新";
    self.table.footerRefreshingText = @"玩命加载中";
    self.table.footerPullToRefreshText = @"下拉开始刷新";
    self.table.footerReleaseToRefreshText = @"松开开始刷新";
}
//刷新和加载方法
- (void)headerRereshing{
    NSLog(@"headerRereshing");
   [self.table headerEndRefreshing];
 //[self.table headerBeginRefreshing];
}
- (void)footerRereshing{
    NSLog(@"footerRereshing");
    [self.table footerEndRefreshing];
    //[self.table footerBeginRefreshing];
}
- (UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath {
    
    NSString *cellIdentifier = @"cell";
    ListCellView *cell = [tableView dequeueReusableCellWithIdentifier:cellIdentifier];
    if (cell == nil)
    {
        cell = (ListCellView *)[[[NSBundle mainBundle]loadNibNamed:@"ListCellView" owner:self options:nil] firstObject];
    }
    //配置cell
    NSDictionary *dic = [NSDictionary dictionaryWithObjectsAndKeys:[self.data objectAtIndex:[indexPath row]],@"title", nil];
    [cell configStyle:dic];
    return cell;
 }
@end

````
