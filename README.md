

#include<iostream>
#include "Vector.h"
using namespace std;


   //returns the current size of the vector
 	template <class T>
    unsigned int Vector<T>::get_size(){
        return size;
     }
     
     //insert element elt at the end of vector
     template <class T>
     void Vector<T>::push_back(const T& elt){

         if((size)+1) >= maxsize){
                resize();

         }
         arr[size]=elt;
         size++;
     }
     
     //delete last element
    template <class T>
    void Vector<T>::pop_back(){

        arr[size-1]=NULL;

     }
     //return reference to element at position pos
    template <class T>
    T& Vector<T>::at(int pos){
        return arr[pos];  //if this doesn't work put *
    }
	//return reference to the first element
	template <class T>
    T& Vector<T>::front(){
        return arr[0];
    }
    //return reference to the last element
    template <class T>
    T& Vector<T>::back(){

        return arr[size-1];
    }
    //return true if vector is empty
    template <class T>
    bool Vector<T>::empty(){
        if(size==0)
            return true;
        return false;
    }

    //delete element at position pos
    template <class T>
    void Vector<T>::insert (const T& elt, int pos){
        T temp[size];
        for(int i=0; i<size; i++){
            temp[i]=arr[i];
        }
        delete [] arr;
        size++;
        arr=new[size];
        for(int i=0; i<pos; i++){
            arr[i]=temp[i];
        }
        arr[pos]=elt;
        for(int i=pos+1; i<size; i++){
            arr[i]=temp[i-1];
        }
    }
    
    template <class T>
    void Vector<T>::erase(int pos){
        for(int i=pos; i<size-1; i++){
            arr[pos]=arr[pos+1];
        }
        size--;
    }

	template <class T>
    void Vector<T>::erase(int pos1, int pos2){
        T temp1 [size];
        T temp2 [size];
            for(int i=0; i<pos1; i++){
                temp1[i]=arr[i];
            }
            int holder=0;
            for(int i=(pos2+1); i<size; i++){
                temp2[holder]=arr[i];
                holder++;
            }
            delete [] arr;
            size=size-(pos2-pos1+1);
            arr= new[size];
            for(int i=0; i<pos1; i++){
                arr[i]=temp1[i]
            }
            holder=0;
            for(int i=pos1; i<size; i++){
                arr[i]=temp2[holder];
                holder++;
            }
    }
/*
     vector& Vector::operator= (const vector<T>& vec){
         for(int i=0; i<)
     }
*/


	template <class T>
	void Vector<T>::resize(){
    	maxsize*=2;
    	T temp[maxsize];
    	for(int i=0; i<size; i++){
            temp[i]=arr[i];
    	}
    	delete [] arr;
    	arr= new[max_size];
    	for(int i=0; i<size; i++){
        	arr[i]=temp[i];
    	}
	}
