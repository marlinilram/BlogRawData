title: smart pointer in c++
date: 2015-08-31 20:53:38
categories: c++
tags: [c++, smart pointer]
---

A code example for smart pointer in c++. [From "Cracking the Code Inerview"]

{% codeblock smart pointer lang:cpp %}
template <class T> class SmartPointer {
public:
    SmartPointer(T * ptr) {
        ref = ptr;
        ref_count = (unsigned*)malloc(sizeof(unsigned));
        *ref_count = 1;
    }
    SmartPointer(SmartPointer<T> & sptr) {
        ref = sptr.ref;
        ref_count = sptr.ref_count;
        ++*ref_count;
    }
    SmartPointer<T> & operator=(SmartPointer<T> & sptr) {
        if (this != &sptr) {
            ref = sptr.ref;
            ref_count = sptr.ref_count;
            ++*ref_count;
        }
        return *this;
    }
    ~SmartPointer() {
        --*ref_count;
        if (*ref_count == 0) {
            delete ref;
            free(ref_count);
            ref = NULL;
            ref_count = NULL;
        }
    }
    T getValue() { return *ref; }
protected:
    T * ref;
    unsigned * ref_count;
};
{% endcodeblock %}