# Libft
> Why using standard libraries, if you can have your own :-P

Of course using the common C libraries such as ```string.h```, ```stdlib.h```, ```unistd.h```, etc. would be quicker... But how do you get into C and best understand the cocept of libraries and the basic functions?

Therefore as a first step in the core curriculum of 42 we had to built our own library with a lot of common functions. The goal is to get familiar with the functions to be able to use them instinctivly in the future. The library is our basis for several projects in the core curriculum.

# Functions

## Libft
<details>
<summary>LibC functions</summary>

- isalpha
- isdigit
- isalnum
- isascii
- isprint
- strlen
- memset
- bzero
- memcpy
- memmove
- strlcpy
- strlcat
- toupper
- tolower
- strchr
- strrchr
- strncmp
- memchr
- memcmp
- strnstr
- atoi
- calloc
- strdup
</details>

<details>
  <summary>Additional functions</summary>

  | Function name | Prototype | Description |
  | ----- | ----- | ----- |
  | ft_substr | `char *ft_substr(char const *s, unsigned int start, size_t len);` | Allocates (with malloc(3)) and returns a substring from the string ’s’. The substring begins at index ’start’ and is of maximum size ’len’. |
  | ft_strjoin | `char *ft_strjoin(char const *s1, char const *s2);` | Allocates (with malloc(3)) and returns a new string, which is the result of the concatenation of ’s1’ and ’s2’. |
  | ft_strtrim | `char *ft_strtrim(char const *s1, char const *set);` | Allocates (with malloc(3)) and returns a copy of ’s1’ with the characters specified in ’set’ removed from the beginning and the end of the string. |
  | ft_split | `char **ft_split(char const *s, char c);` | Allocates (with malloc(3)) and returns an array of strings obtained by splitting ’s’ using the character ’c’ as a delimiter. The array must end with a NULL pointer. |
  | ft_itoa | `char *ft_itoa(int n);` | Allocates (with malloc(3)) and returns a string representing the integer received as an argument. Negative numbers must be handled. |
  | ft_strmapi | `char *ft_strmapi(char const *s, char (*f)(unsigned int, char));` | Applies the function ’f’ to each character of the string ’s’, and passing its index as first argument to create a new string (with malloc(3)) resulting from successive applications of ’f’. |
  | ft_striteri | `void ft_striteri(char *s, void (*f)(unsigned int, char*));` | Applies the function ’f’ on each character of the string passed as argument, passing its index as first argument. Each character is passed by address to ’f’ to be modified if necessary. |
  | ft_putchar_fd | `void ft_putchar_fd(char c, int fd);` | Outputs the character ’c’ to the given file descriptor. |
  | ft_putstr_fd | `void ft_putstr_fd(char *s, int fd);` | Outputs the string ’s’ to the given file descriptor. |
  | ft_putendl_fd | `void ft_putendl_fd(char *s, int fd);` | Outputs the string ’s’ to the given file descriptor followed by a newline. |
  | ft_putnbr_fd | `void ft_putnbr_fd(int n, int fd);` | Outputs the integer ’n’ to the given file descriptor. |
</details>

<details>
  <summary>Additional functions (Lists)</summary>

  The struct refered to in the functions is defined as follows:
  ```
  typedef struct s_list
  {
    void           *content;
    struct s_list  *next;
  }                t_list;
  ```
  
  | Function name | Prototype | Description |
  | ----- | ----- | ----- |
  | ft_lstnew | `t_list *ft_lstnew(void *content);` | Allocates (with malloc(3)) and returns a new node. The member variable ’content’ is initialized with the value of the parameter ’content’. The variable ’next’ is initialized to NULL. |
  | ft_lstadd_front | `void ft_lstadd_front(t_list **lst, t_list *new);` | Adds the node ’new’ at the beginning of the list. |
  | ft_lstsize | `int ft_lstsize(t_list *lst);` | Counts the number of nodes in a list. |
  | ft_lstlast | `t_list *ft_lstlast(t_list *lst);` | Returns the last node of the list. |
  | ft_lstadd_back | `void ft_lstadd_back(t_list **lst, t_list *new);` | Adds the node ’new’ at the end of the list. |
  | ft_lstdelone | `void ft_lstdelone(t_list *lst, void (*del)(void *));` | Takes as a parameter a node and frees the memory of the node’s content using the function ’del’ given as a parameter and free the node. |
  | ft_lstclear | `void ft_lstclear(t_list **lst, void (*del)(void *));` | Deletes and frees the given node and every successor of that node, using the function ’del’ and free(3). Finally, the pointer to the list is set to NULL. |
  | ft_lstiter | `void ft_lstiter(t_list *lst, void (*f)(void *));` | Iterates the list ’lst’ and applies the function ’f’ on the content of each node. |
  | ft_lstmap | `t_list *ft_lstmap(t_list *lst, void *(*f)(void *), void (*del)(void *));` | Iterates the list ’lst’ and applies the function ’f’ on the content of each node. Creates a new list resulting of the successive applications of the function ’f’. The ’del’ function is used to delete the content of a node if needed. |
</details>

## ft_printf
The function `ft_printf` mimics the original `printf` function (from `stdlib.h`). It's prototype is:
```
  int  ft_printf(const char *, ...);
```
`ft_printf` can handle the following conversions: cspdiuxX%

In comparison to the original `printf`, the buffer management is not implemented.


## get_next_line
The function `get_next_line` (prototype: `char *get_next_line(int fd);`) returns a line read from a file descriptor.

The file descriptor `fd` is passed as a parameter. The function returns the value of the read line (correct behavior). `NULL` is returned if there is nothing else to read (end-of-file) or an error occured.

Each call of the function returns the next line of the file descriptor.


# Built, Include and Use

Built the `libft.a`:
1. clone the repo
2. navigate to the folder
3. `make` in terminal

Include the header:
* simply include the header-file `libft.h` (located at the root of libft) for all the functions listed above (including get_next_line und ft_printf)

Use the `libft.a`:
* when compiling you own project, add `-I ./<LIBFT_PATH>` and `<LIBFT_PATH>/libft.a` (or simply `lft)`
* e.g.: `cc -Wall -Werror -Wextra <c-files> -I ./<LIBFT_PATH> lft`


