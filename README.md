# This creates a node class
class Node(object):
    def __init__(self, val):
        self. val = val
        self. next = None

    def get_data(self):
        return self.val

    def set_data(self, val):
        self. val = val

    def get_next(self):
        return self.next

    def set_next(self, next):
        self.next = next


# This creates the Linklist class
class Linklist (object):
    def __init__(self, head=None):
        self.head = head
        self.count = 0

    # This method tells you how many nodes you have
    def get_count(self):
        return self.count

    # This inserts a new node
    def insert(self, data):
        newNode = Node(data)
        newNode.set_next(self.head)
        self.head = newNode
        self.count += 1

    # finds the first item with a given value
    def find(self, val):
        item = self.head
        while (item != None):
            if item.get_data() == val:
                return item
            else:
                item = item.get_next()
        return None

    #  return None
    # deletes items at a given index
    def delete(self, idx):
        if idx > self.count - 1:
            return
        if idx == 0:
            self.head = self.head.get_next()
        else:
            tempidx = 0
            node = self.head
            while tempidx < idx - 1:
                node = node.get_next()
                tempidx += 1
            node = node.set_next(node.get_next().get_next())
            self.count -= 1

    def dumplist(self):
        tempNode = self.head
        while (tempNode != None):
            print("Node", tempNode.get_data())

            tempNode = tempNode.get_next()


# creating a new linklist and inserting to the list
itemList = Linklist()
itemList.insert(38)
itemList.insert(42)
itemList.insert(49)
itemList.insert(13)
itemList.dumplist()

print("Item count in my list", itemList.get_count())
print("find item", itemList.find(42))

itemList.delete(2)
itemList.dumplist()
print("How many items are left on the list", itemList.get_count())
