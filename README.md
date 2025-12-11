# OOP4-2
OOP4, 2
class Instrument:
    def __init__(self, name, play):
        self.name = name
        self.play = play

    def playing(self):
        if self.play:
            print(f"Now playing the {self.name}")

class StringInstrument(Instrument):
    def __init__(self, name, play, numberOfStrings):
        super().__init__(name, play) 
        self.numberOfStrings = numberOfStrings

    def playing(self):
        super().playing() 
        print(f"with {self.numberOfStrings} strings and 1 bow")

violin = StringInstrument("violin", True, 5)
violin.playing()

class MathOperations:
    def findMaximumNumber(self, a, b):
        return max(a, b)

class MathOperationsForLists(MathOperations):
    def findMaximumNumber(self, numbers):
        if len(numbers) == 1:
            return numbers[0]
        else:
            max_of_rest = self.findMaximumNumber(numbers[1:])
            return max(numbers[0], max_of_rest)

math_operations = MathOperationsForLists()

numbers = [10, 5, 20, 8, 15]
result = math_operations.findMaximumNumber(numbers)

print(result)

def remove_non_numbers(lst):
    result = [] 
    for item in lst:
        if type(item) == list: 
            result.append(remove_non_numbers(item))
        elif type(item) == int or type(item) == float: 
            result.append(item)
    return result
input_list = ([[1,2,"text"],["ok",5], ["words",7,8]])
output_list = remove_non_numbers(input_list)

print(output_list)

def sum_values_2DList(lst, sum=0):
    for sublist in lst:
        if type(sublist) == list:
            sum = sum_values_2DList(sublist, sum)
        else:
            sum += sublist
    return sum

print(sum_values_2DList([[1, 2], [3, 4]]))
