#include <GL/gl.h>
#include <GL/glu.h>
#include <GL/glut.h>
#include<math.h>


#include <stdlib.h>
#include <windows.h>
void display();
void reshape(int w,int h);
void timer(int);



void init(){
    glClearColor(164.0/255.0,212.0/255.0 ,224.0/255.0,0.0);
}
int main(int argc,char**argv)
{
    glutInit(&argc,argv);
    glutInitDisplayMode(GLUT_RGB);

    glutInitWindowPosition(200,0);
    glutInitWindowSize(1200,800);

    glutCreateWindow("20101298,20101950");

    glutDisplayFunc(display);
    glutReshapeFunc(reshape);
    glutTimerFunc(0,timer,0);

     init();

    glutMainLoop();
}
float step=0;

void display()
{
    glClear(GL_COLOR_BUFFER_BIT);
    glLoadIdentity();
    glLineWidth(3.0);
    double radius;



 //sand
glPushMatrix();
glBegin(GL_QUADS);
glColor3ub(222, 232 ,86);
glVertex2f(-15,-8);
glVertex2f(15,-8);
glVertex2f(15,-15);
glVertex2f(-15,-15);
glEnd();
glPopMatrix();
//sea
glPushMatrix();
glBegin(GL_QUADS);
glColor3ub(37, 190 ,232);
glVertex2f(-15,-2);
glVertex2f(15,-2);
glVertex2f(15,-8);
glVertex2f(-15,-8);
glEnd();
glPopMatrix();
//boat
glPushMatrix();
glBegin(GL_POLYGON);
glColor3ub(20, 184 ,135);
glVertex2f(-8+step,4);
glVertex2f(8+step,4);
glVertex2f(4+step,-2);
glVertex2f(-4+step,-2);
glEnd();
glPopMatrix();
//flagbody
glPushMatrix();
glBegin(GL_QUADS);
glColor3ub(10, 7 ,6);
glVertex2f(-0.3+step,7);
glVertex2f(0.3+step,7);
glVertex2f(0.3+step,4);
glVertex2f(-0.3+step,4);
glEnd();
glPopMatrix();
//flag
glPushMatrix();
glBegin(GL_POLYGON);
glColor3ub(207, 27 ,27);
glVertex2f(0.3+step,5);
glVertex2f(3+step,6);
glVertex2f(0.3+step,7);
glEnd();
glPopMatrix();
//cloud1
glPushMatrix();
glTranslated(-6+step,8,0);
glBegin(GL_POLYGON);

glColor3ub(255, 255 ,255);
radius=1.5;
for(int i=0;i<360;i++){
    double angle =i*3.14/180;
    glVertex2d(cos(angle)*radius,radius*sin(angle));

}
glEnd();
glPopMatrix();
glPushMatrix();
glTranslated(-7.5+step,8,0);
glBegin(GL_POLYGON);
glColor3ub(255, 255 ,255);
radius=1.5;
for(int i=0;i<360;i++){
    double angle =i*3.14/180;
    glVertex2d(cos(angle)*radius,radius*sin(angle));

}
glEnd();
glPopMatrix();
glPopMatrix();
glPushMatrix();
glTranslated(-9+step,8,0);
glBegin(GL_POLYGON);
glColor3ub(255, 255 ,255);
radius=1.5;
for(int i=0;i<360;i++){
    double angle =i*3.14/180;
    glVertex2d(cos(angle)*radius,radius*sin(angle));

}
glEnd();
glPopMatrix();
//cloud2
glPushMatrix();
glTranslated(-6+step,8,0);
glBegin(GL_POLYGON);
glColor3ub(255, 255 ,255);
radius=1;
for(int i=0;i<360;i++){
    double angle =i*3.14/180;
    glVertex2d(cos(angle)*radius,radius*sin(angle));

}
glEnd();
glPopMatrix();
glPushMatrix();
glTranslated(-7.5+step,8,0);
glBegin(GL_POLYGON);
glColor3ub(255, 255 ,255);
radius=1;
for(int i=0;i<360;i++){
    double angle =i*3.14/180;
    glVertex2d(cos(angle)*radius,radius*sin(angle));

}
glEnd();
glPopMatrix();
glPopMatrix();
glPushMatrix();
glTranslated(-9+step,8,0);
glBegin(GL_POLYGON);
glColor3ub(255, 255 ,255);
radius=1;
for(int i=0;i<360;i++){
    double angle =i*3.14/180;
    glVertex2d(cos(angle)*radius,radius*sin(angle));

}
glEnd();
glPopMatrix();
//cloud2

glPushMatrix();
glTranslated(3+step,8,0);
glBegin(GL_POLYGON);
glColor3ub(255, 255 ,255);
radius=1.5;
for(int i=0;i<360;i++){
    double angle =i*3.14/180;
    glVertex2d(cos(angle)*radius,radius*sin(angle));

}
glEnd();
glPopMatrix();
glPushMatrix();
glTranslated(4.5+step,8,0);
glBegin(GL_POLYGON);
glColor3ub(255, 255 ,255);
radius=1.5;
for(int i=0;i<360;i++){
    double angle =i*3.14/180;
    glVertex2d(cos(angle)*radius,radius*sin(angle));

}
glEnd();
glPopMatrix();
glPopMatrix();
glPushMatrix();
glTranslated(6+step,8,0);
glBegin(GL_POLYGON);
glColor3ub(255, 255 ,255);
radius=1.5;
for(int i=0;i<360;i++){
    double angle =i*3.14/180;
    glVertex2d(cos(angle)*radius,radius*sin(angle));

}
glEnd();
//americanfootball ball
glPushMatrix();
glTranslated(2,-18,0);
glRotated(-19,3.8,6.5,8);
glBegin(GL_POLYGON);
glColor3ub(232, 124 ,9);
radius=0.3;
for(int i=0;i<360;i++){
    double angle =i*3.14/180;
    glVertex2d(cos(angle)+radius,radius*sin(angle));

}
glEnd();





















    glFlush();
}

void reshape(int w,int h)
{
    glViewport(0,0,(GLsizei)w,(GLsizei)h);
    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();
    gluOrtho2D(-15,15,-10,10);
    glMatrixMode(GL_MODELVIEW);
}
void timer(int){
    glutPostRedisplay();
    glutTimerFunc(1000/60,timer,0);
    step+=0.02;
}
