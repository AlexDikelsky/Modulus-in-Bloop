# Modulus-in-Bloop

View as raw

DEFINE PROCEDURE ''MOD'' [N,D]:
BLOCK 0: BEGIN
  LOOP AT MOST N TIMES:
  BLOCK 1: BEGIN
    IF OUTPUT + D > N, THEN:
    BLOCK 2: BEGIN
      OUTPUT <= MINUS[D, MINUS[OUTPUT+D, N]];
      ABORT LOOP 1;
    BLOCK 2: END;
    OUTPUT <= OUTPUT + D
  BLOCK 1: END;
BLOCK 0: END.

DEFINE PROCEDURE ''MINUS'' [X, Y]:
BLOCK 0: BEGIN
  IF X < Y, THEN:
  QUIT BLOCK 0;
  LOOP AT MOST X TIMES:
  BLOCK 1: BEGIN
    IF OUTPUT + Y = X, THEN:
    ABORT LOOP 1;
    OUTPUT <= OUTPUT + 1;
  BLOCK 1: END;
BLOCK 0: END.

MOD[15, 14];
