%% SECANT METHOD
function root = secant(x0,x1,tol,N)
f = @(x) cos(x) - x;
for i = 1:N
x2 = x1 - f(x1)*(x1-x0)/(f(x1)-f(x0));
error = abs(x2-x1);
if error < tol
    break;
end
x0 = x1;
x1 = x2;
end
root = x2;
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
fprintf('root1 = %6f\n',x2);
   

