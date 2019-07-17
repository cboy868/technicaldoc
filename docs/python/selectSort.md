def select_sort(arr):
    for i in range(len(arr)-1):
        minIndex = i
        for j in range(len(arr[:i+1]), len(arr)):
            if arr[minIndex] > arr[j]:
                minIndex = j
        arr[i],arr[minIndex] = arr[minIndex],arr[i]
    return arr



if __name__ == '__main__':
    li = [5, 4,3,2,1]
    li2 = select_sort(li)
    print(li2)


print(list(range(5,-1,-1)))
