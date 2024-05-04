import streamlit as st
import pickle
import pandas as pd




st.title("Movie Recommender System")
movie_dict=pickle.load(open('movie_dict','rb'))
movie=pd.DataFrame(movie_dict)
list=movie["title"].values
similarity=pickle.load(open('similarity','rb'))







def recommend(movie1):
    y=0
    for i in movie["title"].values:
        if (i==movie1):
            break
        else :
            y+=1
    distance=similarity
    l=sorted(enumerate(distance[y]),reverse=True,key=(lambda x:x[1]))
    n=0
    recomend=[]
    for i in l:
        if(n<5):
            recomend.append(movie["title"][i[0]])
            n+=1
        else :
            break
    return recomend




option = st.selectbox(
    "Enter MobileNo",
    list)
if (st.button("prediction")):
    recomend=recommend(option)
    for i in recomend:
        print(i)

# project
