# Leak report

In the beginning, in strip, we see that calloc allocates memory to result, but we can not free result because result is later returned.
Using the valgrind output we go to check the is clean function, and we see that the variable "cleaned" does not get freed after assigning 
a value to it, although we won't need this value after that. So we need to free "cleaned", but we need to check first that cleaned is str
is not an empty string, to avoid getting errors.
