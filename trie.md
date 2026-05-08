```cpp
class TrieNode{
	struct Node {
		int next[26];
		bool end;
		
		Node() {
			memset(next, -1, sizeof(next));
			end = false;
		}
	};
	
	vector<Node> trie;
	
	public:
	Trie() {
		trie.push_back(Node()); // root = 0
	}
	
	void insert(string word){
		int node = 0;
		for(auto& c : word){
			char i = c - 'a';
			if(trie[node].next[i] == -1){
				trie[node].next[i] = trie.size(); // temp->next = new Node();
				trie.push_back(Node());
			}
			node = trie[node].next[i]; // temp = temp->next
		}
		trie[node].end = true;
	}
	
	bool search(string word){
		int node = 0;
		for(auto& c : word){
			char i = c - 'a';
			if(trie[node].next[i] == -1) return false;
		}
		return trie[node].end;
	}
	
	bool startsWith(string prefix){
		int node = 0;
		for(auto& c : prefix){
			char i = c - 'a';
			if(trie[node].next[i] == -1) return false;
		}
		return true;
	}
};
```