# Prática Dart — Mural da Equipe

Repositório-base para a **prática de Git em duplas**: resolução de **conflito de merge** e **Pull Request** — usando o fluxo de **fork**.

O programa `main.dart` monta um "mural" de mensagens da equipe. Ele existe só como **terreno para o conflito** — vocês **não precisam instalar o Dart nem rodar o código**.

> Este é o repositório **original** (upstream). Cada aluno faz um **fork** dele, trabalha no seu fork e abre um **Pull Request** de volta para cá.

---

## O que vocês vão praticar

1. Dar **fork** deste repositório e clonar o seu fork.
2. Criar uma branch e editar **a mesma linha** do `main.dart` que o colega da dupla.
3. A primeira pessoa abre um **Pull Request** para o repositório original → é aprovado (entra sem conflito).
4. A segunda pessoa abre o PR → **conflito!** — sincroniza o fork, resolve na mão e o PR fica pronto.

---

## Passo a passo do fork

**1. Fazer o fork.** No canto superior direito desta página, clique em **Fork → Create fork**. Você terá uma cópia sua: `https://github.com/SEU-USUARIO/pratica-dart`.

**2. Clonar o seu fork** (não o original):

```bash
git clone https://github.com/SEU-USUARIO/pratica-dart.git
cd pratica-dart
```

**3. Apontar para o repositório original (upstream).** Isso permite baixar as mudanças que forem aceitas aqui:

```bash
git remote add upstream https://github.com/USUARIO-DO-PROFESSOR/pratica-dart.git
git remote -v          # confira: origin = seu fork, upstream = o original
```

---

## A linha do conflito

No `main.dart`, procurem o bloco marcado:

```dart
// ===== EDITE A LINHA ABAIXO (a dupla toda edita ESTA mesma linha) =====
'Escreva aqui a saudacao da equipe',
```

As **duas** pessoas da dupla trocam **essa mesma linha** por textos diferentes. Editar a
mesma linha é exatamente o que provoca o conflito de propósito.

---

## Abrir um Pull Request (fork → original)

Depois de commitar e dar `push` na sua branch:

1. Vá até o seu fork no GitHub. Aparece o aviso **"Compare & pull request"** — clique nele.
2. Confirme os campos: **base repository** = repositório do professor, **base** = `main`; **head repository** = o seu fork, **compare** = a sua branch.
3. **Create pull request**. O professor (dono do original) revisa e faz o merge.

---

## Quando der conflito (segunda pessoa da dupla)

Se o GitHub avisar **"This branch has conflicts"**, é porque a mudança da outra pessoa já
entrou no original. Sincronize e resolva localmente:

```bash
git fetch upstream            # busca o que mudou no original
git merge upstream/main       # aqui aparece o CONFLITO
# ... edite o main.dart, apague os marcadores <<<<<<< ======= >>>>>>> ...
git add main.dart
git commit -m "merge: resolve conflito juntando as saudacoes"
git push                      # o mesmo PR se atualiza sozinho e fica pronto
```

---

## Estrutura do projeto

```
.
├── README.md    → este arquivo
└── main.dart    → o "Mural da Equipe" (onde o conflito acontece)
```

---

## Comandos que vocês vão usar

```bash
git clone <url-do-seu-fork>       # copiar o SEU fork
git remote add upstream <url>     # apontar para o repositório original
git switch -c <branch>            # criar e mudar para sua branch
git add main.dart                 # preparar a mudança
git commit -m "feat: ..."         # salvar
git push -u origin <branch>       # enviar a branch para o seu fork
git fetch upstream                # buscar mudanças do original
git merge upstream/main           # juntar o original na sua branch (pode dar conflito)
git status                        # ver o estado — use SEMPRE
```

Na dúvida, rode `git status` e chame o professor.
