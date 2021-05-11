
[org 0]
[bits 16]
	jmp 0x07C0:start



start:
	mov ax, cs
	mov ds, ax

	mov ax, 0xB800
	mov es, ax
	mov di, 0
	mov ax, word [msgBack]
	mov cx, 0x7FF
	
	
	
	
	
paint:
	mov word [es:di], ax
	add di, 2
	dec cx
	
	jnz paint
	
	
	mov edi, 0
	mov byte [es:edi], 'Y'
	inc edi
	mov byte [es:edi], 0x05
	inc edi
	mov byte [es:edi], 'O'
	inc edi
	mov byte [es:edi], 0x16
	inc edi
	mov byte [es:edi], 'U'
	inc edi
	mov byte [es:edi], 0x27
	inc edi
	mov byte [es:edi], 'N'
	inc edi
	mov byte [es:edi], 0x30
	inc edi
	mov byte [es:edi], 'G'
	inc edi
	mov byte [es:edi], 0x41
	inc edi
	
	jmp $
	
	
msgBack db '.', 0x17

times 510-($-$$) db 0


dw 0xAA55