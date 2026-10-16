%% SECANT METHOD
clc;
clear;
f = @(x) cos(x) - x;
x0 = 0;
x1 = 1;
tol = 1e-6;
N = 20;
for i = 1:N
x2 = x1 - f(x1)*(x1-x0)/(f(x1)-f(x0));
error = abs(x2-x1);
if error < tol
    break;
end
x0 = x1;
x1 = x2;
end
fprintf('root = %6f\n',x2);
i = 1;
error = 1;
while error > tol
x2 = x1 - f(x1)*(x1-x0)/(f(x1)-f(x0));
error = abs(x2-x1);
x0 = x1;
x1 = x2;
i = i + 1;
end
fprintf('root = %6f\n',x2);
   


%% NEWTON RAPHSON METHOD
clc;
clear;
y = @(m) m^3 - 2*m - 5;
dy = @(m) 3*m^2 - 2;
m0 = 2;
tol1 = 0.000001;
N1 = 20;
for i = 1:N1
m1 = m0 - y(m0)/dy(m0);
error1 = abs(m1-m0);
if error1 < tol1
    break;
end
m0 = m1;
end
fprintf('root1 = %6y\n',m1);
 R = newtonRaphson(m0,tol1,N1);
 fprintf('root1 = %6y\n',R);
 function root = newtonRaphson(m0,tol1,N1)
y = @(m) m^3 - 2*m - 5;
dy = @(m) 3*m^2 - 2;
for i = 1:N1
m1 = m0 - y(m0)/dy(m0);
error1 = abs(m1-m0);
if error1 < tol1
    break;
end
m0 = m1;
end
root = m1;
 end
 %% NESTED FUNCTION-NRM
 m0 = 2;
 tol1 = 0.000001;
 N1 = 20;
 root = nestedNRM(m0,tol1,N1);
 fprintf('root1 = %6y\n',root);
 function output = nestedNRM(m0,tol1,N1)
 for i = 1:N1
m1 = m0 - y(m0)/dy(m0);
error1 = abs(m1-m0);
if error1 < tol1
    break;
end
m0 = m1;
 end
 output= m1;
     function T = y(m)
         T = m^3 - 2*m - 5;
     end
     function T = dy(m)
        T = 3*m^2 - 2;
     end
 end
 