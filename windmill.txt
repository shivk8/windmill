#include <Windows.h>
#include <GL\glew.h>
#include <GL\freeglut.h>
#include <iostream>
#include<stdlib.h>

using namespace std;

float coords[12] = { 9,9,50,50,0,-10,0,-60,-9,9,-50,50 };
float xr = 5, yr = 5;
void myInit()
{
	glClear(GL_COLOR_BUFFER_BIT);
	glColor3f(1.0f, 1.0f, 1.0f);
	glPointSize(2);
	glMatrixMode(GL_PROJECTION);
	gluOrtho2D(-300, 300, -300, 300);
}

void plot(int a, int b, int xc, int yc)
{
	glBegin(GL_POINTS);
	glColor3f(1.0f, 1.0f, 1.0f);
	glVertex2d(a + xc, b + yc);
	glEnd();


}



void midpoint(int xc, int yc, int r)
{
	int x, y, p;
	p = 1 - r;
	x = 0;
	y = r;
	plot(x, y, xc, yc);
	while (x <= y)
	{
		if (p <= 0)
		{
			x++;
			p += 2 * x + 1;
		}
		else
		{
			x++;
			y--;
			p += 2 * (x - y) + 1;
		}
		plot(x, y, xc, yc);
		plot(x, -y, xc, yc);
		plot(-x, y, xc, yc);
		plot(-x, -y, xc, yc);
		plot(y, x, xc, yc);
		plot(y, -x, xc, yc);
		plot(-y, x, xc, yc);
		plot(-y, -x, xc, yc);
	}

}

void rotateblade(float angles,float tx,float ty)
{
	int i, j;
	double mat[3][3] = { 0.0,0.0,0.0,0.0,0.0,0.0,0.0,0.0,1.0 };
	mat[0][0] = cos(angles);
	mat[0][1] = -sin(angles);
	mat[1][0] = sin(angles);
	mat[1][1] = cos(angles);
	mat[0][2] = tx;
	mat[1][2] = ty;
	double a[3][1], b[3][1];
	int index = 0;
	for (int c = 0; c <= 5; c++)
	{
		if (c == 0)
		{
			a[0][0] = coords[0];
			a[1][0] = coords[1];
			/*if (a[0][0] < a[1][0] && a[0][0]>=0 && a[1][0]>0)
			{
				mat[0][2] = tx;
				mat[1][2] = ty;
			}
			else if (a[0][0] > a[1][0] && a[0][0] > 0 && a[1][0]<=0)
			{
				mat[0][2] = -tx;
				mat[1][2] = ty;
			}
			else if (a[0][0] > a[1][0] && a[0][0] <= 0 && a[1][0] < 0)
			{
				mat[0][2] = -tx;
				mat[1][2] = -ty;
			}
			else if (a[0][0] > a[1][0] && a[0][0] <= 0 && a[1][0] < 0)
			{
				mat[0][2] = tx;
				mat[1][2] = -ty;
			}*/
		}

		if (c == 1)
		{
			a[0][0] = coords[2];
			a[1][0] = coords[3];
			/*if (a[0][0] < a[1][0] && a[0][0]>=0 && a[1][0]>0)
			{
				mat[0][2] = tx;
				mat[1][2] = ty;
			}
			else if (a[0][0] > a[1][0] && a[0][0] > 0 && a[1][0]<=0)
			{
				mat[0][2] = -tx;
				mat[1][2] = ty;
			}
			else if (a[0][0] > a[1][0] && a[0][0] <= 0 && a[1][0] < 0)
			{
				mat[0][2] = -tx;
				mat[1][2] = -ty;
			}
			else if (a[0][0] > a[1][0] && a[0][0] <= 0 && a[1][0] < 0)
			{
				mat[0][2] = tx;
				mat[1][2] = -ty;
			}*/
		}

		if (c == 2)
		{
			a[0][0] = coords[4];
			a[1][0] = coords[5];
			/*if (a[0][0] < a[1][0] && a[0][0]>=0 && a[1][0]>0)
			{
				mat[0][2] = tx;
				mat[1][2] = ty;
			}
			else if (a[0][0] > a[1][0] && a[0][0] > 0 && a[1][0]<=0)
			{
				mat[0][2] = -tx;
				mat[1][2] = ty;
			}
			else if (a[0][0] > a[1][0] && a[0][0] <= 0 && a[1][0] < 0)
			{
				mat[0][2] = -tx;
				mat[1][2] = -ty;
			}
			else if (a[0][0] > a[1][0] && a[0][0] <= 0 && a[1][0] < 0)
			{
				mat[0][2] = tx;
				mat[1][2] = -ty;
			}*/
		}

		if (c == 3)
		{
			a[0][0] = coords[6];
			a[1][0] = coords[7];
			/*if (a[0][0] < a[1][0] && a[0][0]>=0 && a[1][0]>0)
			{
				mat[0][2] = tx;
				mat[1][2] = ty;
			}
			else if (a[0][0] > a[1][0] && a[0][0] > 0 && a[1][0]<=0)
			{
				mat[0][2] = -tx;
				mat[1][2] = ty;
			}
			else if (a[0][0] > a[1][0] && a[0][0] <= 0 && a[1][0] < 0)
			{
				mat[0][2] = -tx;
				mat[1][2] = -ty;
			}
			else if (a[0][0] > a[1][0] && a[0][0] <= 0 && a[1][0] < 0)
			{
				mat[0][2] = tx;
				mat[1][2] = -ty;
			}*/
		}

		if (c == 4)
		{
			a[0][0] = coords[8];
			a[1][0] = coords[9];
			/*if (a[0][0] < a[1][0] && a[0][0]>=0 && a[1][0]>0)
			{
				mat[0][2] = tx;
				mat[1][2] = ty;
			}
			else if (a[0][0] > a[1][0] && a[0][0] > 0 && a[1][0]<=0)
			{
				mat[0][2] = -tx;
				mat[1][2] = ty;
			}
			else if (a[0][0] > a[1][0] && a[0][0] <= 0 && a[1][0] < 0)
			{
				mat[0][2] = -tx;
				mat[1][2] = -ty;
			}
			else if (a[0][0] > a[1][0] && a[0][0] <= 0 && a[1][0] < 0)
			{
				mat[0][2] = tx;
				mat[1][2] = -ty;
			}*/
		}

		if (c == 5)
		{
			a[0][0] = coords[10];
			a[1][0] = coords[11];
			/*if (a[0][0] < a[1][0] && a[0][0]>=0 && a[1][0]>0)
			{
				mat[0][2] = tx;
				mat[1][2] = ty;
			}
			else if (a[0][0] > a[1][0] && a[0][0] > 0 && a[1][0]<=0)
			{
				mat[0][2] = -tx;
				mat[1][2] = ty;
			}
			else if (a[0][0] > a[1][0] && a[0][0] <= 0 && a[1][0] < 0)
			{
				mat[0][2] = -tx;
				mat[1][2] = -ty;
			}
			else if (a[0][0] > a[1][0] && a[0][0] <= 0 && a[1][0] < 0)
			{
				mat[0][2] = tx;
				mat[1][2] = -ty;
			}*/
		}


		a[2][0] = 1.0;
		
		for (i = 0; i < 3; ++i)
		{
			for (j = 0; j < 1; ++j)
			{
				b[i][j] = 0;
				for (int k = 0; k < 3; ++k)
				{
					b[i][j] += mat[i][k] * a[k][j];
				}
			}
			
		}
		coords[index] = b[0][0];
		coords[index + 1] = b[1][0];
		cout << coords[index] << coords[index + 1];
		index += 2;
		
		
	}
}

void myDisplay()
{
	float ang;
	ang = (float)(-20 * 3.14 / 180);
	midpoint(0, 0, 10);
	


	glBegin(GL_LINES);
	glColor3f(1.0f, 1.0f, 1.0f);
	glPointSize(50);
	glVertex2d(9,9);
	glVertex2d(50, 50);
	glEnd();
	glFlush();

	glBegin(GL_LINES);
	glColor3f(1.0f, 1.0f, 1.0f);
	glPointSize(50);
	glVertex2d(0,-10);
	glVertex2d(0,-60);
	glEnd();
	glFlush();

	glBegin(GL_LINES);
	glColor3f(1.0f, 1.0f, 1.0f);
	glPointSize(50);
	glVertex2d(-9,9);
	glVertex2d(-50,50);
	glEnd();
	glFlush();

	glBegin(GL_LINES);
	glColor3f(1.0f, 1.0f, 1.0f);
	glPointSize(50);
	glVertex2d(0,-10);
	glVertex2d(0,-70);
	glEnd();
	glFlush();

	glBegin(GL_LINES);
	glColor3f(1.0f, 1.0f, 1.0f);
	glPointSize(50);
	glVertex2d(-10, -70);
	glVertex2d(10, -70);
	glEnd();
	glFlush();
	int count = 6;
	while (count>=0)
	{
		Sleep(200);
		glClear(GL_COLOR_BUFFER_BIT);
		rotateblade(ang,0.5,-0.5);

		midpoint(0, 0, 10);
		glBegin(GL_LINES);
		glColor3f(1.0f, 1.0f, 1.0f);
		glPointSize(50);
		glVertex2d(coords[0],coords[1]);
		glVertex2d(coords[2], coords[3]);
		glEnd();
		glFlush();


		glBegin(GL_LINES);
		glColor3f(1.0f, 1.0f, 1.0f);
		glPointSize(50);
		glVertex2d(coords[4], coords[5]);
		glVertex2d(coords[6], coords[7]);
		glEnd();
		glFlush();

		glBegin(GL_LINES);
		glColor3f(1.0f, 1.0f, 1.0f);
		glPointSize(50);
		glVertex2d(coords[8], coords[9]);
		glVertex2d(coords[10], coords[11]);
		glEnd();
		glFlush();

		glBegin(GL_LINES);
		glColor3f(1.0f, 1.0f, 1.0f);
		glPointSize(50);
		glVertex2d(0, -10);
		glVertex2d(0, -70);
		glEnd();
		glFlush();

		glBegin(GL_LINES);
		glColor3f(1.0f, 1.0f, 1.0f);
		glPointSize(50);
		glVertex2d(-10, -70);
		glVertex2d(10, -70);
		glEnd();
		glFlush();

		

	}
}

int main(int argc, char** argv)
{
	glutInit(&argc, argv);
	glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB);
	glutInitWindowSize(600, 600);
	glutCreateWindow("windmill");
	glutDisplayFunc(myDisplay);
	myInit();
	glutMainLoop();
	return 1;
}