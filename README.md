def comma(s):
    for i in s:
        if i[-1] == ',':
            actual_word = i
            word = i[:-1:]
            ind = s.index(actual_word)
            for i in s:
                if i == word and (i[-1] != '.' or i[-1] != ','):
                    k = i+','
                    s = [k if ((i == word) and s[-1] != i) else i for i in s]
    l=[]
    for i in s:
        ind = s.index(i)
        if ind>0:
            prev_word = s[ind-1]
            if ((prev_word[-1] == ',') and (prev_word[-1] != '.') and s[0] != i):
                if(i[-1]=='.'):
                    i=i[:-1:]
                l.append(i)
                l.append(i+'.')
    indices = [index for index, value in enumerate(s) if value in l]
    for i in indices:
        prev_word=s[i-1]
        s=[(j+',') if j==prev_word and prev_word[-1]!=',' and prev_word[-1]!='.' else j for j in s]
    s1=' '.join(s)
    return s1
s = input().split()
a = comma(s)
p=a.split()
print(comma(p))
