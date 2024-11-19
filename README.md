#include<iostream>
int roll, semester, session, t_subj, t_marks=150;
	char name[15], Fname[15], program[10];
	struct subjects{
		char sub_name[20];
		int obt_marks;
		char grade;
		float subj_gpa;
		float total_gpa;
		int crd_hrs;
	};
void enterDetails(){
	printf("Enter Registration #: ");
	scanf("%d",&roll);
	printf("Enter Student's Name: ");
	scanf("%s",name);
	printf("Enter Father's Name: ");
	scanf("%s",Fname);
	printf("Enter Semester: ");
	scanf("%d",&semester);
	printf("Enter Session: ");
	scanf("%d",&session);
	printf("Enter Degree Program: ");
	scanf("%s",program);
	
}
char calculateGrade(int marks)
	{
		if(marks>=90)
		return 'A';
		else if(marks>=80)
		return 'B';
		else if(marks>=70)
		return 'C';
		else if(marks>=60)
		return 'D';
		else
		return 'F';
		
	}
	
	float calculateGPA(char grade)
	{
	if(grade=='A')
	return 4.0;
	else if(grade=='B')
	return 3.0;
	else if(grade=='C')
	return 2.0;
	else if(grade=='D')
	return 1.0;
	else
	return 0.0;	
	}

	void subjDetails(struct subjects sub[]){
		for(int i=1; i<=t_subj; i++)
		{
		printf("Enter name of Subject %d: ",i);
		scanf("%s",sub[i].sub_name);
		printf("Enter Obtained marks: ");
		scanf("%d",&sub[i].obt_marks);
		printf("Enter credit hours: ");
		scanf("%d",&sub[i].crd_hrs);
		sub[i].grade = calculateGrade(sub[i].obt_marks);
		sub[i].subj_gpa = calculateGPA(sub[i].grade);
		}
	}
	
	
	
	void displayResult(struct subjects sub[])
	{
		
		printf("\t\t XYZ University\n");
		printf("______________________________________________\n\n");
		printf("Roll#: %d",roll);
		printf("\t\t");
		printf("Name: %s %s\n",name ," ",Fname);
		printf("Program: %s",program);
		printf("\t\t");
		printf("Session: %d\n",session);
		printf("Semester: %d",semester);
		printf("\t\t");
		printf("Courses: %d\n",t_subj);
		printf("_____________________________________________\n");
		printf("\n");
		printf("\n");
		printf("Subject \t TotalMarks ObtainedMarks Grade GP\n");
		for(int i=1; i<=t_subj; i++)
		{
			
			printf("%s",sub[i].sub_name);
			printf(" \t ");
			printf("%d",t_marks);
			printf("\t");
			printf("%d",sub[i].obt_marks);
			printf("\t");
			printf("%c",sub[i].grade);
			printf("\t");
			printf("%d",sub[i].subj_gpa);
			
			printf("\n");
	
		}
		
	}
	
	

int main()
{
	struct subjects sub[5];
	char cont = 'y';
	int choice;
	printf("\tStudent Result Card Generation\n");
	printf("\tMENU\n");
	printf("\t1 - Enter Student Details\n");
	printf("\t2 - Generete Result Card\n");
	while(cont == 'y' || cont == 'Y')
	{
		printf("Enter choice: ");
		scanf("%d",&choice);
		if(choice==1)
		{
			enterDetails();
			printf("Enter total number of subjects: ");
			scanf("%d",&t_subj);
			subjDetails(sub);
			printf("Record saved successfully\n");
		
		}
		
		if(choice==2){
			displayResult(sub);
		}
	
		printf("Want to continue? press y");
		scanf(" %c",&cont);
	
	
}
	return 0;
}
