```c++

void dfs(int a,int b){
    for (int i=0; i<NUM_POINTS; i++) {
        if (flag) {
            return;
        }
        cout<<"现在在判断Matrix"<<a<<i<<"是不是1"<<endl;
        if (!matrix[a][i]) {
            cout<<"它是0"<<endl;
            visited[a][i]=1;
            visited[i][a]=1;
            cout<<"visited数组变成1"<<endl;
            if (i==NUM_POINTS-1) {
                cout<<"是最后一个元素 判断栈是否为空"<<endl;
                if (!s.is_empty()) {
                    cout<<"不为空 准备初始化本行 出栈"<<endl;
                    for (int j=0; j<NUM_POINTS; j++) {
                        visited[a][j]=0;
                    }
                    cout<<s.read()<<"即将出栈"<<endl;
                    dfs(s.pop(), b);
                }
                else {
                    cout<<"栈为空 返回"<<endl;
                    flag=1;
                }
            }
            else {
                cout<<"不是最后一个 继续判断下一个i"<<endl;
                continue;
            }
        }
        else{
            cout<<"它是1"<<endl;
            cout<<"现在在判断visited"<<a<<i<<"是不是1"<<endl;
            if (!visited[a][i]) {
                cout<<"他是0 判断i是否存在栈中"<<endl;
                if (s.do_have(i)) {
                    cout<<"i存在于栈中 跳过 判断下一个i"<<endl;
                    continue;
                }
                else {
                    cout<<"不存在栈中 判断是否与目的地相等"<<endl;
                    if(i==b){
                        cout<<"与目的地相等 visited变为1"<<endl;
                        visited[a][i]=1;
                        visited[i][a]=1;
                        cout<<"get"<<endl;
                        cout<<"判断是否是最后一个元素"<<endl;
                        if (i==NUM_POINTS-1) {
                            cout<<"是最后一个元素 判断栈是否为空"<<endl;
                            if (!s.is_empty()) {
                                cout<<"不为空 准备初始化本行 出栈"<<endl;
                                for (int j=0; j<NUM_POINTS; j++) {
                                    visited[a][j]=0;
                                }
                                cout<<s.read()<<"即将出栈"<<endl;
                                dfs(s.pop(), b);
                            }
                            else {
                                cout<<"栈为空 返回"<<endl;
                                flag=1;
                            }
                        }
                        else {
                            cout<<"不是最后一个 继续判断下一个i"<<endl;
                            continue;
                        }
                        
                    }
                    else{
                        cout<<"i不等于b visited变成1 准备进入"<<i<<endl;
                        visited[a][i]=1;
                        visited[i][a]=1;
                        path.push(a);
                        s.push(a);
                        cout<<a<<"已进栈 进行遍历"<<i<<endl;
                        dfs(i, b);
                    }
                }
            }
            else {
                cout<<"他是1 已经被访问 判断他是最后一个"<<endl;
                if(i==NUM_POINTS-1){
                    cout<<"他是最后一个 判断栈是否为空"<<endl;
                    if (!s.is_empty()) {
                        cout<<"栈不为空 初始化本行"<<endl;
                        for (int j=0; j<NUM_POINTS; j++) {
                            visited[a][j]=0;
                        }
                        cout<<"准备出栈 开始遍历"<<s.read()<<endl;
                        dfs(s.pop(), b);
                    }
                    else {
                        cout<<"栈为空 结束"<<endl;
                        flag=1;
                    }
                }
                else {
                    cout<<"不是最后一个 继续判断下一个i"<<endl;
                    continue;
                }
            }
        }
    }
}


```


in:
0 1 0 1 1
1 0 1 1 0
0 1 0 1 0
1 1 1 0 1
1 0 0 1 0
请输入DFS起止点
0 2
现在在判断Matrix00是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix01是不是1
它是1
现在在判断visited01是不是1
他是0 判断i是否存在栈中
不存在栈中 判断是否与目的地相等
i不等于b visited变成1 准备进入1
0已进栈 进行遍历1
现在在判断Matrix10是不是1
它是1
现在在判断visited10是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix11是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix12是不是1
它是1
现在在判断visited12是不是1
他是0 判断i是否存在栈中
不存在栈中 判断是否与目的地相等
与目的地相等 visited变为1
get
判断是否是最后一个元素
不是最后一个 继续判断下一个i
现在在判断Matrix13是不是1
它是1
现在在判断visited13是不是1
他是0 判断i是否存在栈中
不存在栈中 判断是否与目的地相等
i不等于b visited变成1 准备进入3
1已进栈 进行遍历3
现在在判断Matrix30是不是1
它是1
现在在判断visited30是不是1
他是0 判断i是否存在栈中
i存在于栈中 跳过 判断下一个i
现在在判断Matrix31是不是1
它是1
现在在判断visited31是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix32是不是1
它是1
现在在判断visited32是不是1
他是0 判断i是否存在栈中
不存在栈中 判断是否与目的地相等
与目的地相等 visited变为1
get
判断是否是最后一个元素
不是最后一个 继续判断下一个i
现在在判断Matrix33是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix34是不是1
它是1
现在在判断visited34是不是1
他是0 判断i是否存在栈中
不存在栈中 判断是否与目的地相等
i不等于b visited变成1 准备进入4
3已进栈 进行遍历4
现在在判断Matrix40是不是1
它是1
现在在判断visited40是不是1
他是0 判断i是否存在栈中
i存在于栈中 跳过 判断下一个i
现在在判断Matrix41是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix42是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix43是不是1
它是1
现在在判断visited43是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix44是不是1
它是0
visited数组变成1
是最后一个元素 判断栈是否为空
不为空 准备初始化本行 出栈
3即将出栈
现在在判断Matrix30是不是1
它是1
现在在判断visited30是不是1
他是0 判断i是否存在栈中
i存在于栈中 跳过 判断下一个i
现在在判断Matrix31是不是1
它是1
现在在判断visited31是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix32是不是1
它是1
现在在判断visited32是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix33是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix34是不是1
它是1
现在在判断visited34是不是1
他是1 已经被访问 判断他是最后一个
他是最后一个 判断栈是否为空
栈不为空 初始化本行
准备出栈 开始遍历1
现在在判断Matrix10是不是1
它是1
现在在判断visited10是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix11是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix12是不是1
它是1
现在在判断visited12是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix13是不是1
它是1
现在在判断visited13是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix14是不是1
它是0
visited数组变成1
是最后一个元素 判断栈是否为空
不为空 准备初始化本行 出栈
0即将出栈
现在在判断Matrix00是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix01是不是1
它是1
现在在判断visited01是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix02是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix03是不是1
它是1
现在在判断visited03是不是1
他是0 判断i是否存在栈中
不存在栈中 判断是否与目的地相等
i不等于b visited变成1 准备进入3
0已进栈 进行遍历3
现在在判断Matrix30是不是1
它是1
现在在判断visited30是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix31是不是1
它是1
现在在判断visited31是不是1
他是0 判断i是否存在栈中
不存在栈中 判断是否与目的地相等
i不等于b visited变成1 准备进入1
3已进栈 进行遍历1
现在在判断Matrix10是不是1
它是1
现在在判断visited10是不是1
他是0 判断i是否存在栈中
i存在于栈中 跳过 判断下一个i
现在在判断Matrix11是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix12是不是1
它是1
现在在判断visited12是不是1
他是0 判断i是否存在栈中
不存在栈中 判断是否与目的地相等
与目的地相等 visited变为1
get
判断是否是最后一个元素
不是最后一个 继续判断下一个i
现在在判断Matrix13是不是1
它是1
现在在判断visited13是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix14是不是1
它是0
visited数组变成1
是最后一个元素 判断栈是否为空
不为空 准备初始化本行 出栈
3即将出栈
现在在判断Matrix30是不是1
它是1
现在在判断visited30是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix31是不是1
它是1
现在在判断visited31是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix32是不是1
它是1
现在在判断visited32是不是1
他是0 判断i是否存在栈中
不存在栈中 判断是否与目的地相等
与目的地相等 visited变为1
get
判断是否是最后一个元素
不是最后一个 继续判断下一个i
现在在判断Matrix33是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix34是不是1
它是1
现在在判断visited34是不是1
他是0 判断i是否存在栈中
不存在栈中 判断是否与目的地相等
i不等于b visited变成1 准备进入4
3已进栈 进行遍历4
现在在判断Matrix40是不是1
它是1
现在在判断visited40是不是1
他是0 判断i是否存在栈中
i存在于栈中 跳过 判断下一个i
现在在判断Matrix41是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix42是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix43是不是1
它是1
现在在判断visited43是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix44是不是1
它是0
visited数组变成1
是最后一个元素 判断栈是否为空
不为空 准备初始化本行 出栈
3即将出栈
现在在判断Matrix30是不是1
它是1
现在在判断visited30是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix31是不是1
它是1
现在在判断visited31是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix32是不是1
它是1
现在在判断visited32是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix33是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix34是不是1
它是1
现在在判断visited34是不是1
他是1 已经被访问 判断他是最后一个
他是最后一个 判断栈是否为空
栈不为空 初始化本行
准备出栈 开始遍历0
现在在判断Matrix00是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix01是不是1
它是1
现在在判断visited01是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix02是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix03是不是1
它是1
现在在判断visited03是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix04是不是1
它是1
现在在判断visited04是不是1
他是0 判断i是否存在栈中
不存在栈中 判断是否与目的地相等
i不等于b visited变成1 准备进入4
0已进栈 进行遍历4
现在在判断Matrix40是不是1
它是1
现在在判断visited40是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix41是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix42是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix43是不是1
它是1
现在在判断visited43是不是1
他是0 判断i是否存在栈中
不存在栈中 判断是否与目的地相等
i不等于b visited变成1 准备进入3
4已进栈 进行遍历3
现在在判断Matrix30是不是1
它是1
现在在判断visited30是不是1
他是0 判断i是否存在栈中
i存在于栈中 跳过 判断下一个i
现在在判断Matrix31是不是1
它是1
现在在判断visited31是不是1
他是0 判断i是否存在栈中
不存在栈中 判断是否与目的地相等
i不等于b visited变成1 准备进入1
3已进栈 进行遍历1
现在在判断Matrix10是不是1
它是1
现在在判断visited10是不是1
他是0 判断i是否存在栈中
i存在于栈中 跳过 判断下一个i
现在在判断Matrix11是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix12是不是1
它是1
现在在判断visited12是不是1
他是0 判断i是否存在栈中
不存在栈中 判断是否与目的地相等
与目的地相等 visited变为1
get
判断是否是最后一个元素
不是最后一个 继续判断下一个i
现在在判断Matrix13是不是1
它是1
现在在判断visited13是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix14是不是1
它是0
visited数组变成1
是最后一个元素 判断栈是否为空
不为空 准备初始化本行 出栈
3即将出栈
现在在判断Matrix30是不是1
它是1
现在在判断visited30是不是1
他是0 判断i是否存在栈中
i存在于栈中 跳过 判断下一个i
现在在判断Matrix31是不是1
它是1
现在在判断visited31是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix32是不是1
它是1
现在在判断visited32是不是1
他是0 判断i是否存在栈中
不存在栈中 判断是否与目的地相等
与目的地相等 visited变为1
get
判断是否是最后一个元素
不是最后一个 继续判断下一个i
现在在判断Matrix33是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix34是不是1
它是1
现在在判断visited34是不是1
他是1 已经被访问 判断他是最后一个
他是最后一个 判断栈是否为空
栈不为空 初始化本行
准备出栈 开始遍历4
现在在判断Matrix40是不是1
它是1
现在在判断visited40是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix41是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix42是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix43是不是1
它是1
现在在判断visited43是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix44是不是1
它是0
visited数组变成1
是最后一个元素 判断栈是否为空
不为空 准备初始化本行 出栈
0即将出栈
现在在判断Matrix00是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix01是不是1
它是1
现在在判断visited01是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix02是不是1
它是0
visited数组变成1
不是最后一个 继续判断下一个i
现在在判断Matrix03是不是1
它是1
现在在判断visited03是不是1
他是1 已经被访问 判断他是最后一个
不是最后一个 继续判断下一个i
现在在判断Matrix04是不是1
它是1
现在在判断visited04是不是1
他是1 已经被访问 判断他是最后一个
他是最后一个 判断栈是否为空
栈为空 结束
Program ended with exit code: 0