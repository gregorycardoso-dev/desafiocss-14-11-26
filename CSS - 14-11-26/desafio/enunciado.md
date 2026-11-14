# Desafio final — DevDay

Você recebeu o HTML, as cores e as fontes da página de um evento. Falta o layout, e ele é seu.

Abra `index.html` e escreva o CSS depois do comentário `SEU CSS AQUI`.

## Regras

- Não mexa no HTML nem no CSS da base.
- **Primeiros 5 minutos sem teclado.** No papel, para cada seção: circule o pai e responda as 4 perguntas.
- Comece pelo celular: DevTools, modo de dispositivo, 375px.
- Travou? Cola, depois DevTools, depois o colega. Só então o professor, e ele vai responder com uma pergunta.

## As 4 perguntas

1. Quem é o pai?
2. Linha, coluna ou grade?
3. Como distribuo o espaço?
4. E quando a tela muda?

---

## Nível 1 — Celular (375px)

```
┌────────────────────────────┐
│          <DevDay/>         │
│ Palestrantes Agenda Ingres.│
├────────────────────────────┤
│                            │
│      14 de março de 2027   │
│    Um dia inteiro de...    │
│    [ Garantir ingresso ]   │
│                            │
├────────────────────────────┤
│ Palestrantes               │
│ ┌────────────────────────┐ │
│ │         (foto)         │ │
│ │      Marina Duarte     │ │
│ │  Arquitetura de front  │ │
│ └────────────────────────┘ │
│ ┌────────────────────────┐ │
│ │         (foto)         │ │
│ │          ...           │ │
├────────────────────────────┤
│ Agenda                     │
│ 09:00  Abertura     Saguão │
│ 10:00  Front-end... Audit. │
├────────────────────────────┤
│   © 2027 DevDay — evento   │
│    [ Comprar ingresso ]    │
└────────────────────────────┘
```

1. **Topo:** logo em cima, menu embaixo, os dois centralizados, com `0.5rem` entre eles.
2. **Menu:** os três links em linha, com `1.25rem` entre eles.
3. **Hero:** ocupa pelo menos 60% da altura da janela. Data, título e botão empilhados no centro exato, na horizontal e na vertical, com `1rem` entre eles.
4. **Palestrantes:** um cartão por linha, com `1.25rem` entre os cartões.
5. **Cada cartão:** foto, nome e tema empilhados e centralizados, com `0.5rem` entre eles.
6. **Cada linha da agenda:** horário, título e sala na mesma linha, com `1rem` entre eles e alinhados pelo centro. O título ocupa todo o espaço que sobrar, empurrando a sala para a direita.
7. **Rodapé:** texto em cima, botão embaixo, centralizados, com `0.75rem` entre eles.

---

## Nível 2 — Telas maiores

```
┌──────────────────────────────────────────────────────────────┐
│ <DevDay/>                     Palestrantes  Agenda  Ingressos │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│                    14 de março de 2027                       │
│            Um dia inteiro de código, café e gente boa        │
│                   [ Garantir ingresso ]                      │
│                                                              │
├──────────────────────────────────────────────────────────────┤
│ Palestrantes                                                 │
│ ┌────────────┐ ┌────────────┐ ┌────────────┐ ┌────────────┐  │
│ │   (foto)   │ │   (foto)   │ │   (foto)   │ │   (foto)   │  │
│ │    Nome    │ │    Nome    │ │    Nome    │ │    Nome    │  │
│ └────────────┘ └────────────┘ └────────────┘ └────────────┘  │
├──────────────────────────────────────────────────────────────┤
│ Agenda                                                       │
│ 09:00  Abertura e café                                Saguão │
│ 10:00  Front-end que escala sem virar bagunça      Auditório │
├──────────────────────────────────────────────────────────────┤
│ © 2027 DevDay — evento fictício        [ Comprar ingresso ]  │
└──────────────────────────────────────────────────────────────┘
```

**A partir de 768px**

8. **Topo:** logo à esquerda, menu à direita, na mesma linha.
9. **Palestrantes:** dois cartões por linha.
10. **Rodapé:** texto à esquerda, botão à direita, na mesma linha.

**A partir de 1024px**

11. **Palestrantes:** quatro cartões por linha.

---

## Nível 3 — Acabamento

12. A etiqueta "Keynote" fica no canto superior direito do cartão, a `0.75rem` das bordas, sem empurrar a foto.
13. O topo acompanha a rolagem, grudado no alto da janela, e nada passa por cima dele.

---

## Antes de entregar

- [ ] Testei em 375, 768, 1024 e 1280px.
- [ ] Em nenhuma largura aparece rolagem para o lado.
- [ ] Consigo explicar cada regra que escrevi com as 4 perguntas.
