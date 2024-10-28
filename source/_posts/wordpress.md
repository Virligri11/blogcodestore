---
title: NLP test
date: 2024-08-26 16:30:30
tags: NLP
---


'''python
import pandas as pd
import jieba
from sklearn.feature_extraction.text import TfidfVectorizer, CountVectorizer
from sklearn.decomposition import LatentDirichletAllocation
import pyLDAvis  
import pyLDAvis.lda_model# sklearn change to lda model
pyLDAvis.enable_notebook()  

'''

using jieba to cut the chinese words
'''python 
def chinese_word_cut(mytext):  
    return " ".join(jieba.cut(mytext))
'''

'''
n_features = 1000
tf_vectorizer = CountVectorizer(strip_accents = 'unicode',  #编码格式
                                max_features=n_features,  #最大值
                                stop_words='english',  #跳过英文
                                max_df = 0.5,  
                                min_df = 10)  
tf = tf_vectorizer.fit_transform(df.content_cutted)
n_topics = 10
lda = LatentDirichletAllocation(n_components=n_topics, max_iter=50,  
                                learning_method='online',  
                                learning_offset=50.,  
                                random_state=0)
lda.fit(tf)

'''

'''
tf_feature_names = tf_vectorizer.get_feature_names_out()  

def print_top_words(model, feature_names, n_top_words):  
    for topic_idx, topic in enumerate(model.components_):  
        print("Topic #%d:" % topic_idx)  
        print(" ".join([feature_names[i]for i in topic.argsort()[:-n_top_words - 1:-1]]))  
    print()

print_top_words(lda,tf_feature_names,20)
'''