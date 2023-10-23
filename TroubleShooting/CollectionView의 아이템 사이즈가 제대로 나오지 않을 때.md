CollectionView의 아이템 사이즈가 제대로 나오지 않을 때
==================

문제 발생 : 

코드는 제대로 입력햤는데, CollectionView의 아이템 사이즈가 제대로 나오지 않는다.

</br>

```swift

func collectionView(_ collectionView: UICollectionView, layout collectionViewLayout: UICollectionViewLayout, sizeForItemAt indexPath: IndexPath) -> CGSize {
        let width = collectionView.frame.width
        let interSpacing: CGFloat = 20
        let lineCount: CGFloat = 3
        let totalWidth = width - (interSpacing * (lineCount - 1))
        let itemSize = totalWidth / lineCount
        
        return CGSize(width: itemSize, height: itemSize)
}

```

</br>

![스크린샷 2023-09-26 오후 6 01 46](https://github.com/pursWon/won_TIL/assets/99719661/c1d802d7-7b5d-41b7-9d87-33fcfc35db90)


</br>

cell의 사이즈를 지정하는데에 있어서 코드는 문제가 없는데, cell이 화면에서 제대로 출력이 되지 않을 때,

</br>

CollectionView의 Estimate Size가 None으로 되있는지 확인하자
