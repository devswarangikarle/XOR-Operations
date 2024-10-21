# XOR-Operations

Ram purchased N integers A1, A2,. ., AN for new year party. Now he wants to perform some function on the numbers. More specifically, he wants to calculate the sum of all the XOR of a number with the numbers to its right i.e. XOR the number with all the numbers to its right and add the value to the final answer. Since the answer can be very large, take its modulus with 109 + 7. This operation is valid for every integer except the last one (since there is no number to the right of the last number). Calculate the final sum.

MOD = 10**9 + 7

def xor_sum(A, N):

    result = 0
    
    for bit in range(61):
        count_ones = 0
        
        for num in A:
            if num & (1 << bit):
                count_ones += 1
        
        count_zeros = N - count_ones
        
        bit_contribution = count_ones * count_zeros * (1 << bit)
        result = (result + bit_contribution) % MOD
    
    return result

N = int(input())
A = list(map(int, input().split()))

print(xor_sum(A, N))
