# No more LOOP AT SCREEN #

To handle selection screens using "LOOP AT SCREEN" statement can be very boring and it consumes some time when developing and maintaining such logic. If you work on complicated screens the screens logic become opacity.

Imagine that you have selection screen with two radio buttons and two input fields. When the first radio button is selected, the first input field is open for input only. When the second radio button is selected, the second input field is open for input only. How would you match this result by old way?

```
PARAMETERS: x_opt_1 RADIOBUTTON GROUP opt USER-COMMAND option_selected.
PARAMETERS: p_carrid TYPE scarr-carrid.
PARAMETERS: x_opt_2 RADIOBUTTON GROUP opt DEFAULT 'X'.
SELECT-OPTIONS: s_carrid FOR p_carrid.

AT SELECTION-SCREEN OUTPUT.
  LOOP AT SCREEN.
    CASE screen-name.
      WHEN 'P_CARRID'.
        IF x_opt_1 = 'X'.
          screen-input = 1.
        ELSE.
          screen-input = 0.
        ENDIF.
      WHEN 'S_CARRID-LOW'.
        IF x_opt_1 = 'X'.
          screen-input = 0.
        ELSE.
          screen-input = 1.
        ENDIF.
      WHEN 'S_CARRID-HIGH'.
        IF x_opt_1 = 'X'.
          screen-input = 0.
        ELSE.
          screen-input = 1.
        ENDIF.
      WHEN OTHERS.
    ENDCASE.
    MODIFY SCREEN.
  ENDLOOP.

START-OF-SELECTION.
* your code here ...
```

**And now, try it with new code:**

```
REPORT  zsbdemo.

DATA: r_screen TYPE REF TO zcl_screen_breaker.

PARAMETERS: x_opt_1 RADIOBUTTON GROUP opt USER-COMMAND option_selected,
            p_carrid TYPE scarr-carrid,
            x_opt_2 RADIOBUTTON GROUP opt DEFAULT 'X'.
SELECT-OPTIONS: s_carrid FOR p_carrid.

INITIALIZATION.
  CREATE OBJECT r_screen.

AT SELECTION-SCREEN OUTPUT.
  IF x_opt_1 = 'X'.
    r_screen->set_input( 'P_CARRID' ).
    r_screen->set_output( 'S_CARRID-LOW' ).
    r_screen->set_output( 'S_CARRID-HIGH' ).
    r_screen->activate_screen( ).
  ENDIF.

  IF x_opt_2 = 'X'.
    r_screen->set_output( 'P_CARRID' ).
    r_screen->set_input( 'S_CARRID-LOW' ).
    r_screen->set_input( 'S_CARRID-HIGH' ).
    r_screen->activate_screen( ).
  ENDIF.

START-OF-SELECTION.

* your code here …
```

Which code do you like more? It's up to you :-)