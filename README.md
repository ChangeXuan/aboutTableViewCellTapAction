# aboutTableViewCellTapAction
## 昨晚上遇到了一个小问题，在这里做一个简单的记录，免得自己忘了
背景是这样的，我有两个界面(viewController)，第一个节目的主要内容是一个TableView，第二个界面只有一个简单的Label，也就是说，我在第二个界面并没有什么耗时的代码。我想达到的效果是，当我点击第一个界面的cell的时候，跳转到第二个界面。但是当我执行点击这个动作的时候，系统并没有立刻执行跳转，而是像被卡顿了一样，又或者是等一段时间后才跳转成功。刚刚开始我以为是什么内存问题，或者是什么引用问题，但是排查之后，都否认了。最后在网上找到了答案。
### 当cell的selectionStyle属性设置为.none时会出现该情况
然后我把cell的selectionStyle设置成了.default，问题解决

(ps:因为一般的cell点击后会一直取得那个位置的焦点，所以为了美观，我在didSelectRowAt这个协议函数中添加了这句   tableView.deselectRow(at:indexPath,animated:true))
