# Replication file for: "Some DIY Cryptography in Python"
# RPubs-link: https://rpubs.com/mstefan-rpubs/ciphers
# (c) Martin Stefan, June 2020

import string

class Caesar:

	def encipher(plain, s):
	    alpha = string.ascii_lowercase
	    subst = alpha[s:] + alpha[:s]
	    cipher = []
	    for i in plain:
	    	letter = subst[alpha.find(i)]
	    	cipher.append(letter)
	    return ''.join(cipher)

	def decipher(cipher, s):
	    plain = Caesar.encipher(cipher,-s)
	    return plain

print(Caesar.decipher(Caesar.encipher("helloworld",5),5))



class Polybius:

	def encipher(plain, keyword):

		# create secret alphabet => 5x5 square
		square = []
		for c in keyword + string.ascii_lowercase:
			if c not in square and c != "j":
				square.append(c)
		square = ''.join(square)

		# loop through plain text to encipher
		cipher = []
		for i in plain:
			n = square.find(i) + 1
			row,col = divmod(n,5)
			cipher.append(str(row+1)+str(col))

		# return
		return cipher

	def decipher(cipher, keyword):

		# create secret alphabet => 5x5 square
		square = []
		for c in keyword + string.ascii_lowercase:
			if c not in square and c != "j":
				square.append(c)
		square = ''.join(square)

		# loop through cipher text to decipher
		plain = []
		for i in range(len(cipher)):
			row = int(cipher[i][0])
			col = int(cipher[i][1])
			letter = square[(row-1)*5 + col-1]
			plain.append(letter)

		# return
		return "".join(plain)

print(Polybius.decipher(Polybius.encipher("helloworld","polybius"),"polybius"))



class Vigenere:

	def encipher(plain, keyword):
		n = 0
		alpha = string.ascii_lowercase
		cipher = []
		for i in plain:
			if n > len(keyword)-1:
				n = 0
			s = alpha.find(keyword[n])
			letter = Caesar.encipher(i, s)
			cipher.append(letter)
			n += 1
		return ''.join(cipher)

	def decipher(cipher, keyword):
		n = 0
		alpha = string.ascii_lowercase
		plain = []
		for i in cipher:
			if n > len(keyword)-1:
				n = 0
			s = alpha.find(keyword[n])
			letter = Caesar.decipher(i, s)
			plain.append(letter)
			n += 1
		return ''.join(plain)

print(Vigenere.decipher(Vigenere.encipher("helloworld","vigenere"),"vigenere"))
