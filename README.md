# 2Dwordsearch
# WORD SEARCH
# RESULT is boolean either TRUE or FALSE
# A class is defined by defining the classname to be WordSearch
class Wordsearch:
    
    #Function givenword is defined
    def givenword(self, board, w, c, i, j, v):
        if c == len(w):# if the current is equal to the length of the given word
            return True #return true
        #if any of the condition is satisfied then return falpse
        if i < 0 or i >= len(board) or j < 0 or j >= len(board[0]) or v[i][j] or board[i][j] != w[c]:
            return False
        
        v[i][j] = True
        # the result is assigned with the appropriate result 
        result = self.givenword(board, w, c + 1, i + 1, j, v) or\
                 self.givenword(board, w, c + 1, i - 1, j, v) or\
                 self.givenword(board, w, c + 1, i, j + 1, v) or\
                 self.givenword(board, w, c + 1, i, j - 1, v)         
        v[i][j] = False
        return result
#Function givenboard is defined with the par 
    def givenboard(self, board, w):
        v = [[False for j in range(len(board[0]))]
             for i in range(len(board))]
       
        for i in range(len(board)):
            for j in range(len(board[0])):
                if self.givenword(board, w, 0, i, j, v):
                    
                    return True
        
        return False
    
if __name__ == "__main__":

    rows=1# the row is assigned to 1 as to display 1 row of string inside the list assigned to board
    col=1 #column is assigned to 1

    board = [ "ABCE",
              "SFCS",
              "ADEE"
            ]#given board with the stringin a list
    for i in range(rows):
        
       
     for j in range(col):
          
      print "2D BOARD"
      print "********"
      print '\n'
      print(board)# print the board with the strrings on the given board
     print '\n'#new line
     #Calling the function givenboard 
    print "Given a word ABCCED =", Wordsearch().givenboard(board, "ABCCED")
    print "Given a word SEE =", Wordsearch().givenboard(board, "SEE")
    print "Given a word ABCB =", Wordsearch().givenboard(board, "ABCB")
