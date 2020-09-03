---
title: Vue d’ensemble du protocole de serveur de langage | Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3bd5dce3cfb7022a8abb6397dc87b418144cbe1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703103"
---
# <a name="language-server-protocol"></a>Protocole de serveur de langage

## <a name="what-is-the-language-server-protocol"></a>Qu’est-ce que le protocole du serveur de langage ?

La prise en charge des fonctionnalités d’édition enrichies, telles que la saisie semi-automatique de code source ou l' **accès à la définition** d’un langage de programmation dans un éditeur ou un IDE, est généralement très complexe et fastidieuse. En règle générale, il est nécessaire d’écrire un modèle de domaine (un scanneur, un analyseur, un vérificateur de type, un générateur, etc.) dans le langage de programmation de l’éditeur ou de l’IDE. Par exemple, le plug-in Eclipse CDT, qui assure la prise en charge de C/C++ dans l’IDE Eclipse, est écrit en Java, car l’IDE Eclipse lui-même est écrit en Java. En suivant cette approche, vous devez implémenter un modèle de domaine C/C++ dans TypeScript pour Visual Studio code et un modèle de domaine distinct en C# pour Visual Studio.

La création de modèles de domaine spécifiques à une langue est également beaucoup plus facile si un outil de développement peut réutiliser des bibliothèques existantes propres à un langage. Toutefois, ces bibliothèques sont généralement implémentées dans le langage de programmation lui-même (par exemple, les bons modèles de domaine C/C++ sont implémentés en C/C++). L’intégration d’une bibliothèque C/C++ dans un éditeur écrit dans la machine à écrire est techniquement possible, mais difficile à faire.

### <a name="language-servers"></a>Serveurs de langue

Une autre approche consiste à exécuter la bibliothèque dans son propre processus et à utiliser la communication entre processus pour y communiquer. Les messages envoyés à l’arrière-plan forment un protocole. Le protocole de serveur de langue (LSP) est le produit de standardiser les messages échangés entre un outil de développement et un processus de serveur de langage. L’utilisation de serveurs de langue ou de Demons n’est pas une idée nouvelle ou nouvelle. Les éditeurs comme vim et Emacs ont fait cela depuis un certain temps pour fournir une prise en charge de la saisie semi-automatique sémantique. L’objectif du LSP était de simplifier ces types d’intégration et de fournir une infrastructure utile pour exposer les fonctionnalités de langage à un large éventail d’outils.

Le fait de disposer d’un protocole commun permet d’intégrer des fonctionnalités de langage de programmation dans un outil de développement avec un minimum de tracas en réutilisant une implémentation existante du modèle de domaine du langage. Un serveur de langage principal peut être écrit en PHP, Python ou Java et le LSP permet de l’intégrer facilement à un large éventail d’outils. Le protocole fonctionne à un niveau d’abstraction commun afin qu’un outil puisse offrir des services de langage riche sans avoir à comprendre pleinement les nuances spécifiques au modèle de domaine sous-jacent.

## <a name="how-work-on-the-lsp-started"></a>Mode de démarrage du travail sur le LSP

Le LSP a évolué au fil du temps et est aujourd’hui à la version 3,0. Il a commencé lorsque le concept de serveur de langage a été récupéré par OmniSharp pour fournir des fonctionnalités d’édition riches en C#. Au départ, OmniSharp utilisait le protocole HTTP avec une charge utile JSON et a été intégré à plusieurs éditeurs, y compris [Visual Studio code](https://code.visualstudio.com).

En même temps, Microsoft a commencé à travailler sur un serveur de langage de type de machine à écrire, avec l’idée de prendre en charge la machine à écrire dans des éditeurs tels que Emacs et sublime Text. Dans cette implémentation, un éditeur communique via stdin/stdout avec le processus de serveur de machine à écrire et utilise une charge utile JSON inspirée par le protocole de débogueur V8 pour les demandes et les réponses. Le serveur de machine à écrire a été intégré dans le plug-in de sous-chaux d’une machine d’intégration et VS Code pour la modification de la rédaction.

Une fois que vous avez intégré deux serveurs de langues différents, l’équipe de VS Code a commencé à explorer un protocole de serveur de langage commun pour les éditeurs et les IDE. Un protocole commun permet à un fournisseur de langages de créer un serveur de langage unique qui peut être consommé par différents IDE. Un consommateur de serveur de langage ne doit implémenter qu’une seule fois le côté client du protocole. Cela aboutit à une situation gagnante pour le fournisseur de langage et le consommateur de langage.

Le protocole du serveur de langage a démarré avec le protocole utilisé par le serveur de machine à écrire, ce qui l’étend avec davantage de fonctionnalités de langage inspirées par l’API VS Code Language. Le protocole est associé à JSON-RPC pour l’appel à distance en raison de sa simplicité et des bibliothèques existantes.

L’équipe VS Code a prototype le protocole en implémentant plusieurs serveurs de langue Lint qui répondent aux demandes adressées à un fichier (analyser) et retournent un ensemble d’avertissements et d’erreurs détectés. L’objectif était de déformer un fichier à la modification de l’utilisateur dans un document, ce qui signifie qu’il y aura de nombreuses demandes inutilisées lors d’une session de l’éditeur. Il est logique de garder un serveur opérationnel afin qu’il ne soit pas nécessaire de démarrer un nouveau processus Lint pour chaque modification de l’utilisateur. Plusieurs serveurs linters ont été implémentés, y compris les extensions ESLint et TSLint de VS Code. Ces deux serveurs Linter sont tous les deux implémentés dans la machine à écrire/JavaScript et s’exécutent sur Node.js. Ils partagent une bibliothèque qui implémente la partie client et serveur du protocole.

## <a name="how-the-lsp-works"></a>Fonctionnement du LSP

Un serveur de langage s’exécute dans son propre processus, et des outils tels que Visual Studio ou VS Code communiquent avec le serveur à l’aide du protocole de langage sur JSON-RPC. Un autre avantage du serveur de langage fonctionnant dans un processus dédié est que les problèmes de performances liés à un modèle de processus unique sont évités. Le canal de transport réel peut être stdio, Sockets, canaux nommés ou IPC node si le client et le serveur sont tous deux écrits en Node.js.

Vous trouverez ci-dessous un exemple de communication entre un outil et un serveur de langage au cours d’une session de modification de routine :

![diagramme de Flow LSP](media/lsp-flow-diagram.png)

* **L’utilisateur ouvre un fichier (appelé document) dans l’outil**: l’outil avertit le serveur de langage qu’un document est ouvert (« TextDocument/didOpen »). À partir de maintenant, la vérité sur le contenu du document n’est plus sur le système de fichiers, mais est conservée par l’outil en mémoire.

* **L’utilisateur apporte des modifications**: l’outil avertit le serveur de la modification du document (« TextDocument/didChange ») et les informations sémantiques du programme sont mises à jour par le serveur de langue. Dans ce cas, le serveur de langage analyse ces informations et avertit l’outil avec les erreurs et les avertissements détectés (« textDocument/publishDiagnostics »).

* **L’utilisateur exécute « atteindre la définition » sur un symbole dans l’éditeur**: l’outil envoie une demande « textDocument/définition » avec deux paramètres : (1) l’URI du document et (2) la position du texte à partir de laquelle la demande d’accès à la définition a été lancée sur le serveur. Le serveur répond avec l’URI de document et la position de la définition du symbole à l’intérieur du document.

* **L’utilisateur ferme le document (fichier)**: une notification « TextDocument/didClose » est envoyée à partir de l’outil, en informant le serveur de langage que le document n’est plus en mémoire et que le contenu actuel est désormais à jour dans le système de fichiers.

Cet exemple montre comment le protocole communique avec le serveur de langage au niveau des fonctionnalités de l’éditeur telles que « atteindre la définition », « rechercher toutes les références ». Les types de données utilisés par le protocole sont l’éditeur ou les types de données de l’IDE, comme le document texte actuellement ouvert et la position du curseur. Les types de données ne sont pas au niveau d’un modèle de domaine du langage de programmation qui fournit généralement des arborescences de syntaxe abstraites et des symboles de compilateur (par exemple, les types résolus, les espaces de noms, etc.). Cela simplifie considérablement le protocole.

Examinons à présent la demande « textDocument/définition » plus en détail. Voici les charges utiles qui passent entre l’outil client et le serveur de langage pour la demande « atteindre la définition » dans un document C++.

Voici la requête :

```json
{
    "jsonrpc": "2.0",
    "id" : 1,
    "method": "textDocument/definition",
    "params": {
        "textDocument": {
            "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/use.cpp"
        },
        "position": {
            "line": 3,
            "character": 12
        }
    }
}
```

Voici la réponse :

```json
{
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/provide.cpp",
        "range": {
            "start": {
                "line": 0,
                "character": 4
            },
            "end": {
                "line": 0,
                "character": 11
            }
        }
    }
}
```

Dans Retrospect, la description des types de données au niveau de l’éditeur plutôt qu’au niveau du modèle de langage de programmation est l’une des raisons pour la réussite du protocole du serveur de langage. Il est bien plus simple de normaliser un URI de document texte ou une position de curseur par rapport à la normalisation d’une arborescence de syntaxe abstraite et de symboles de compilateur dans différents langages de programmation.

Quand un utilisateur travaille avec différentes langues, VS Code démarre généralement un serveur de langage pour chaque langage de programmation. L’exemple ci-dessous montre une session dans laquelle l’utilisateur travaille sur des fichiers Java et SASS.

![Java et Sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Fonctions

Tous les serveurs de langue ne peuvent pas prendre en charge toutes les fonctionnalités définies par le protocole. Par conséquent, le client et le serveur annoncent leur ensemble de fonctionnalités pris en charge via « Capabilities ». Par exemple, un serveur annonce qu’il peut gérer la demande « textDocument/définition », mais il peut ne pas gérer la demande « espace de travail/symbole ». De même, les clients peuvent annoncer qu’ils sont en mesure de fournir des notifications sur l’enregistrement avant l’enregistrement d’un document, afin qu’un serveur puisse calculer des modifications textuelles afin de mettre en forme automatiquement le document modifié.

## <a name="integrating-a-language-server"></a>Intégration d’un serveur de langue

L’intégration réelle d’un serveur de langage à un outil particulier n’est pas définie par le protocole du serveur de langage et est laissée aux implémenteurs d’outils. Certains outils intègrent les serveurs de langue de façon générique en ayant une extension capable de démarrer et de communiquer avec n’importe quel type de serveur de langage. D’autres, comme VS Code, créent une extension personnalisée par serveur de langage, afin qu’une extension puisse toujours fournir des fonctionnalités de langage personnalisées.

Pour simplifier l’implémentation des serveurs et des clients de langage, il existe des bibliothèques ou des kits de développement logiciel (SDK) pour les composants client et serveur. Ces bibliothèques sont fournies pour différentes langues. Par exemple, il existe un [module Language client NPM](https://www.npmjs.com/package/vscode-languageclient) pour faciliter l’intégration d’un serveur de langage dans une extension de vs code et un [module NPM Language Server](https://www.npmjs.com/package/vscode-languageserver) pour écrire un serveur de langage à l’aide de Node.js. Il s’agit de la [liste](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) actuelle des bibliothèques de prise en charge.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Utilisation du protocole de serveur de langage dans Visual Studio

* [Ajout d’une extension de protocole de serveur de langage](adding-an-lsp-extension.md) : Découvrez comment intégrer un serveur de langage à Visual Studio.
