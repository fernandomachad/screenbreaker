# Introduction #

**Screen Breaker** basically encapsulates a screen state from an ABAP program into an object. This reffered state is represented by the internal table _screen_ which contains properties values for each field in the screen. This page show all the available properties for screen field (i.e. parameters and selection options).


# SCREEN Structure #

Each screen field property is represented by each component in data type _SCREEN_ (see it in ABAP Dictionary - transaction code: SE11). Before see the examples below, consider a fast look in this structure.

# Properties #

| **Property** | **Meaning** | **Possible Values** |
|:-------------|:------------|:--------------------|
| NAME         | Screen field name. For fields expliced declared with keywords as 'PARAMETERS' or 'SELECT-OPTIONS' this is the name of the variable. In case of auxiliar fields not created by custom ABAP code this name varies.  | Any name accepted by ABAP compiler  |
| GROUP1       | ?           | ?                   |
| GROUP2       | ?           | ?                   |
| GROUP3       | ?           | ?                   |
| GROUP4       | ?           | ?                   |
| REQUIRED     | This flag is used to mark a screen field as required  | 0 = Not required  1 = Required|
| INPUT        |             |                     |
| OUTPUT       |             |                     |
| INTENSIFIED  |             |                     |
| INVISIBLE    |             |                     |
| LENGTH       |             |                     |
| ACTIVE       |             |                     |
| DISPLAY\_3D  |             |                     |
| VALUE\_HELP  |             |                     |
| REQUEST      |             |                     |
| VALUES\_IN\_COMBO |             |                     |
| COLOR        |             |                     |