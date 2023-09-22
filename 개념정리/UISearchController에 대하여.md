UISearchController에 대하여
================

<img width="755" alt="스크린샷 2023-01-04 오후 6 12 57" src="https://user-images.githubusercontent.com/99719661/210556293-dd836ecf-17c3-4568-8a70-aa4e66a1e444.png">

검색 창을 기반으로 상호작용하여 나온 검색 결과를 관리하는 뷰 컨트롤러이다.   

검색 창을 만들 때에는 UISearchController를 이용하여 만들어준다. UISearchController가 SearchBar를 내포하고 있다.

</br>

```swift
let searchController = UISearchController(searchResultsController: nil)
self.navigationItem.searchController = searchController
searchController.searchBar.placeholder = "책 이름을 입력해주세요."
```

만들어준 후에 네비게이션 아이템에 들어가 있는 searchController에 지정시켜주면 된다.

그리고, 검색창에 text를 입력할 때마다 tableView가 업데이트 되는 메소드를 쓰자. 

```swift
func setupSearchCotroller() {
        let searchController = UISearchController(searchResultsController: nil)
        searchController.searchBar.placeholder = "책 이름을 입력해주세요."
        searchController.hidesNavigationBarDuringPresentation = true
        searchController.searchResultsUpdater = self
        
        self.navigationItem.searchController = searchController
        self.navigationItem.title = "도서 검색"
        self.navigationItem.hidesSearchBarWhenScrolling = false
    }
```

```swift 

override func viewDidLoad() {
setupSearchCotroller()
}
```

searchController.searchResultsUpdater = self ✅

searchController가 UISearchResultsUpdating를 준수하게 하고 ViewController가 UISearchResultsUpdating의 Delegate가 되도록 설정해주면 된다.

```swift 
extension SearchViewController: UISearchResultsUpdating {
    func updateSearchResults(for searchController: UISearchController) {
        guard let text = searchController.searchBar.text else { return }
    }
}

```



