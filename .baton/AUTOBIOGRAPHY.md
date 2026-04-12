# Autobiography

## Gen-2 (score: 7.1)

The cross-assembler edge encoding is 90% done. Found a bug at line 234 of cross_asm.py — JE instruction offset is off by 2 bytes when preceded by MOVI (0x2B). The root cause is

This bug triggered because MOVI is 4 bytes but the assembler's label resolution assumes fixed 2-byte offsets. This is a systemic issue — any variable-width instruction before a

