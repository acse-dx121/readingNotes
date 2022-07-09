# BackTracking

## Basic Knowledge

### Data structure

#### 字典树

```cpp
class Trie {
private:
    bool isEnd;
    vector<Trie*> children; // 小写字母：26位

    // 前缀搜索
    // 如果搜索到了， 返回尾节点
    // 如果没有搜索到， 返回空节点
    Trie* searchPrefix(string word) {
        Trie* ans = this;

        for(auto w: word) {
            int pref = w - 'a';
            if(ans -> children[pref] == nullptr) {
                return nullptr;
            } 

            ans = ans -> children[pref];
        }

        return ans;
    }
public:
    Trie() {
        children = vector<Trie*>(26, nullptr);
        isEnd = false;
    }

    void insert(string word) {
        Trie* curr = this;

        for(auto w: word) {
            int pref = w - 'a';

            if(curr -> children[pref] == nullptr) {
                curr -> children[pref] = new Trie();
            }

            curr = curr -> children[pref];
        }

        curr -> isEnd = true;
    }

    bool search(string word) {
        auto res = this -> searchPrefix(word);

        return res != nullptr && res -> isEnd;
    }

    bool startsWith(string prefix) {
        auto res = this -> searchPrefix(prefix);
        return res != nullptr;
    }
};

/**
 * Your Trie object will be instantiated and called as such:
 * Trie* obj = new Trie();
 * obj->insert(word);
 * bool param_2 = obj->search(word);
 * bool param_3 = obj->startsWith(prefix);
 */
```

#### 回溯算法框架

```cpp

```
