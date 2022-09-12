# FREE CODE CAMP PYTHON COURSE
# PROJECT: Arithmetic Arranger
# AUTHOR: itstalmeez

def arithmetic_arranger(expression, result=False):
    """
    Arithmetic Arranger\n
    Accepts a list of arithmetic expressions and returns a string of the arithmetic expression arranged vertically.\n
    If more than one expressions are present in the list, each of the vertically arranged expressions are arranged horizontally,\n
    seperating each expresssion from each other.
    \te.g.
    >>> arithmetic_arranger(["32 + 698", "3801 - 2", "45 + 43", "123 + 49"])
       32      3801      45      123
    + 698    -    2    + 43    +  49
    -----    ------    ----    -----

    \n\nCall the function with a second boolean argument set to True, returns a string of arranged expressions togther with their evaluations
    >>> arithmetic_arranger(["32 - 23", "1 - 3801", "9999 + 9999", "523 - 49"], True)
      32         1      9999      523
    - 23    - 3801    + 9999    -  49
    ----    ------    ------    -----
       9     -3800     19998      474
    ----    ------    ------    -----

    """
    if len(expression) > 7:
        return "Error: Too many problems."


    line1 = ""
    line2 = ""
    line3 = ""
    line4 = ""
    for exp in expression:
        exp = exp.replace(" ", "")


        if "+" in exp:
            exp = exp.split(
                "+")
            operator = "+"
        elif "-" in exp:
            exp = exp.split("-")
            operator = "-"
        else:
            return "Error: Operator must be '+' or '-'."


        if not (exp[0].isdigit() and exp[
            1].isdigit()):
            return "Error: Numbers must only contain digits."


        if len(exp[0]) > 6 or len(
                exp[1]) > 6:
            return "Error: Numbers cannot be more than six digits."

        align = max([len(exp[0]), len(exp[
                                          1])]) + 2

        if result:
            res = str(eval(exp[0] + operator + exp[
                1]))
            line4 += res.rjust(
                align) + "    "

        line1 += exp[0].rjust(align) + "    "
        line2 += operator + exp[1].rjust(
            align - 1) + "    "
        line3 += "-" * (align) + "    "





    line1 = line1.rstrip()
    line2 = line2.rstrip()
    line3 = line3.rstrip()

    arranged_string = "\n".join(
        [line1, line2, line3])

    if result:
        line4 = line4.rstrip()
        arranged_string += "\n" + line4 + "\n" + line3

    return arranged_string
