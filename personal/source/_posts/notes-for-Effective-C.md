title: notes for Effective C++
date: 2015-09-05 11:48:14
categories: c++
tags: [c++, effective c++]
---

Part III Resource Management

Item 13: Use objects to manage resources
	Try to use std::TR1::shared_ptr to hold objects

Item 15: Provide access to raw resources in resouce-managing classes
	Use explicit/implicit conversions
	
Item 54: 熟悉TR1
	小技巧，在std名空间内使用boost
	namespace std {
		namespace tr1 = ::boost;
	}