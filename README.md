# ClassicPC360 v2.8b

Projeto experimental de compatibilidade para executar software clássico de PC no Xbox 360 RGH.

## Estado atual

A versão de desenvolvimento **v2.8b** implementa leitura do diretório PE32 Base Relocation e suporte limitado a `IMAGE_REL_BASED_HIGHLOW` (tipo 3), além de entradas `IMAGE_REL_BASED_ABSOLUTE` (tipo 0). O carregador pode usar uma base alternativa quando `ImageBase` não cabe na memória convidada e rejeita imagens que precisem ser deslocadas sem diretório de relocação válido.

## Testes verificados no host

- Graphics smoke test: PASS
- x86 extended test: PASS
- DOS MZ loader test: PASS
- PE32 parser/RVA test: PASS
- PE32 image loader test: PASS
- PE32 import resolver test: PASS
- Kernel32 virtual API test: PASS
- Stack/MOVZX/MOVSX smoke test: PASS
- Xenon platform host smoke test: PASS

## Limitações

O interpretador x86, o carregador PE32, as APIs Win32 e a camada Xenon são parciais. Ainda não há runtime Windows completo, TLS/SEH nem carregamento completo de DLLs. A toolchain Xenon/libXenon não estava disponível no ambiente de validação; portanto não há confirmação de ELF Xenon nem de `default.xex` funcional. Os testes de host não comprovam execução no Xbox 360 RGH nem compatibilidade com jogos comerciais.

O pacote de fontes desta versão é disponibilizado nesta conversa como **ClassicPC360_v2.8b.zip**. O código completo precisa ser sincronizado ao repositório em uma etapa de publicação dedicada.