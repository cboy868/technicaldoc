def insertionSort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        while j >= 0 and key < arr[j]:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key
    return arr



if __name__ == '__main__':
    li = [5, 4,3,2,1,99]
    li2 = insertionSort(li)
    print(li2)


