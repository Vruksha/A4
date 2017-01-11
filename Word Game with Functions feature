''' This code will import a list of words and clean the data to get rid of words that are a repitition of the same letter. The data will then be tested.
In the game, the user will be given two random letters from the alphabet. They must enter a word that begins with the first letter given and ends with the
second letter given. Upon entering the word, the user will be awarded points based on attributes such as word length and whether the word is found in the
imported list. The user will be able to play a maximum of five rounds after which the total score will be displayed. '''


#Import the word list that will be later validated
import urllib.request
import random

#Reading the word list
def readWordList():
    response = urllib.request.urlopen("http://www.mit.edu/~ecprice/wordlist.10000")
    html = response.read()
    data = html.decode('utf-8').split()
    return data

#Cleansing the function of words that are a repetition of the same letter
def cleanse():
    data = readWordList()
    newData = []; #empty list for new data
    count = 0
    for word in data:
        count = 0 # reset count for each new word
        for i in word:
            if i == word[0]:#if any letter in the 
                count = count +1
 
        if count != len(word):  #once the whole word has been iterated over do check
            newData.append(word) #add word to new cleansed word list
    return(newData)
    
#Creating a test function that will test a small portion of the larger list
def testFunction():

    fakeList = urllib.request.urlopen("http://www.cs.queensu.ca/home/cords2/shortList.txt")
    html = fakeList.read()
    fakeData = html.decode('utf-8').split()

    cleanse(fakeData)

    print(fakeData)

#Creating a function to call random letters from the alphabet
def randomLetter():
    data = cleanse()
    alphabet = "abcdefghijklmnopqrstuvwxyz" #Setting up a string variable of all the letters in the alphabet

    L1n = random.randint(0,25) 
    L1 = alphabet[L1n]

    L2w = random.randint(0,25)
    L2 = alphabet[L2w]

    print('These are your letters',L1,'and',L2,'.') #Give the user the two letters

    word = input("Please enter word that begins with letter one and ends with letter two:")

    print("Your Round Score is: ", roundScore(word))
    return(word)

#Creating a function to keep track of score for each round
def roundScore(word):
    newData = cleanse()
    score = 0
    
#Letter values given 
    
    letterValues = [['a',1],['b',2],['c',3],['d',4],['e',5],['f',6],['g',7],['h',8],['i',9],['j',10],['k',11],['l',12],['m',13],['n',14],['o',15],['p',16],['q',17],
                    ['r',18],['s',19],['t',20],['u',21],['v',22],['w',23],['x',24],['y',25],['z',26]]


    if len(word) == 6: #If the word is 6 characters, give the user 3 points
        score = score + 3

    elif len(word) == 7:#If the word is 7 characters, give the user 4 points
        score = score + 4
        
    elif len(word) == 8:#f the word is 8 characters, give the user 5 points
        score = score + 5

    elif len(word) > 8:#If the word is greater than 8 words, give the user 6 points
        score = score + 6

    if word[0] == word[-1]:#If the first and last letter are the same, give the user 10 points
        score = score + 10

    if word not in newData:#If the word is not in the new data list, subtract 10 points
        score = score - 10

    for i in word:#Give the user points for each letter based on the letterValues list above
        for j in letterValues:
            if i in j:
                score = score + j[1]

    return (score)

#sets up the game so that the user can play no more than 5 rounds   
def main():
    cleanse()
    counter = 0 #Initializing the counter to 0 first
    totalScore = 0 #initializes total score 

    while counter !=5: #Ask the user if they would like to play another round only if the counter does not equal 0 
        nxtround = input("Would you like to play another round? Please enter yes or no.")
        if nxtround == "yes":
            word = randomLetter()
            totalScore = totalScore + roundScore(word) #Print the total score if the user wants to quit program

        elif nxtround == "no":
            print ('Your final score is', totalScore,".")
            exit()
            
        counter = counter + 1

    print ("Your final score is: ", totalScore) #print the final score at the end of 5 rounds

main()
