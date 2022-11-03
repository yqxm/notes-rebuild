- #+BEGIN_PINNED
  Sedgewick, R., & Wayne, K. (2012). 算法 (谢路云, Trans.; 4th ed.). 人民邮电出版社.p455-458
  #+END_PINNED
- *概念*
	- 假设一组有键值的元素，要对其按键排序。
		- 首先对键进行计数，
		- 根据计数情况，得到每一个键的起始索引。
		- 创建一个辅助数组，遍历元素，根据键的索引将元素放入辅助数组中。每安排一个元素，更新与之对应的键的索引。
		- 将辅助数组的元素复制进原始数组中完成排序。
- *例子*
	- ```text
	  // 有20个学生，对他们按照分组1~4排序，
	  Anderson        2
	  Brown           3
	  Davis           3
	  Garcia          4
	  Harris          1
	  Jackson         3
	  Johnson         4
	  Jones           3
	  Martin          1
	  Martinez        2
	  Miller          2
	  Moore           1
	  Robinson        2
	  Smith           4
	  Taylor          3
	  Thomas          4
	  Thompson        4
	  White           2
	  Williams        3
	  Wilson          4
	  ```
	- **计数**
		- 创建`count`数组，遍历学生们统计每个组的人数。
		- ```Java
		  // 总共有4个组，为了与组名数字对应，不使用count[0]。
		  // 统计每个组的人数，使用s.Key()+1是为了后面方便计算起始索引。所以count长度为6
		  int[] count = new int[6];
		  for (Student s : students) {
		    count[s.Key()+1]++;
		  }
		  ```
	- **建立索引**
		- ```Java
		  // 为每个键设置它的初始索引。
		  for (int i = 1; i <= 4; i++) {
		    count[i] += count[i-1];
		  }
		  ```
	- **利用辅助数组排序**
		- ```Java
		  Student[] aux = new Student[students.length];
		  for(Student stu : students) {
		    aux[count[stu.Key()]++] = stu;
		  }
		  ```
	- **写回**
		- ```Java
		  for (int i = 0; i < students.length; i++) {
		    students[i] = aux[i];
		  }
		  ```