class Stack:
    def __init__(self):
        self._size = 0
        self._data = []
    
    def getLen(self):
        return self._size
    
    def top(self):
        if self._size == 0:
            return None
        return self._data[-1]
    
    def pop(self):
        if self._size == 0:
            return None
        self._size -= 1
        return self._data.pop()
    
    def push(self, data):
        self._data.append(data)
        self._size += 1
    
    def printData(self):
        for i in range(1, self._size + 1):
            print(self._data[-i])

def printDataPertama(stack: Stack):
    temp_stack = Stack()
    
    # Pindahkan semua elemen dari stack asli ke stack sementara
    while stack.getLen() > 0:
        temp_stack.push(stack.pop())
    
    # Elemen pertama yang dimasukkan adalah yang terakhir dipindahkan
    first_element = temp_stack.top()
    
    # Kembalikan semua elemen dari stack sementara ke stack asli
    while temp_stack.getLen() > 0:
        stack.push(temp_stack.pop())
    
    # Print elemen pertama yang dimasukkan
    print(first_element)

if __name__ == "__main__":
    # Test Case pada program
    # jangan diganti. jika mau diganti, harus dikembalikan
    # ke keadaan semula saat pengumpulan
    
    # mengisi stack
    s = Stack()
    s.push(1)
    s.push(2)
    s.push(1.5)
    s.push(5)
    s.push(3)

    print("Data stack")
    s.printData()
    print()
    print("Menampilkan Data stack paling bawah")
    printDataPertama(s)
    print()
    print("Pembuktian bahwa isi stack tidak berubah")
    s.printData()
