---
title: Vue d’ensemble du protocole Language Server | Documents Microsoft
ms.custom: ''
ms.date: 11/14/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: de7de0ce4d37ed74a7d2291ecf2f0db98c07478b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31147090"
---
# <a name="language-server-protocol"></a>Protocole de serveur de langage

## <a name="what-is-the-language-server-protocol"></a>Qu’est le protocole de serveur langue ?

Prise en charge de riches fonctionnalités d’édition comme automatique de code source-réussies ou **atteindre la définition** pour un langage de programmation dans un éditeur ou un IDE est généralement très difficile et fastidieuse. Elle nécessite généralement l’écriture d’un modèle de domaine (un scanneur, un analyseur, un outil d’analyse de type, un générateur et bien plus encore) dans le langage de programmation de l’éditeur ou l’IDE. Par exemple, le plug-in Eclipse CDT, qui fournit la prise en charge pour C/C++ dans l’IDE Eclipse est écrit en Java, car l’IDE Eclipse lui-même est écrit en langage Java. Suite de cette approche, il signifie implémentation d’un modèle de domaine dans TypeScript pour Visual Studio Code C/C++ et un modèle de domaine distincts en c# pour Visual Studio.

Création de modèles de domaine spécifique à la langue est également beaucoup plus facile si un outil de développement peut réutiliser des bibliothèques spécifiques au langage existantes. Toutefois, ces bibliothèques sont généralement implémentées dans le langage de programmation (par exemple, C/C++ domaine modèles sont implémentés en C/C++). Intégration d’une bibliothèque C/C++ dans un éditeur écrit dans TypeScript est techniquement possible mais difficile.

### <a name="language-servers"></a>Serveurs de langue

Une autre approche consiste à exécuter la bibliothèque dans son propre processus et de communication inter-processus permet de communiquer avec lui. Les messages envoyés dans les deux sens forment un protocole. Le protocole de serveur de langage (LSP) est le produit de la normalisation des messages échangés entre un outil de développement et un processus de serveur de langue. À l’aide de serveurs de langue ou fées n’est pas une idée nouvelle ou nouvelle. Éditeurs, comme Vim et Emacs ont été cette opération pendant un certain temps prendre en charge la sémantique de saisie semi-automatique. L’objectif de LSP était pour simplifier ces types d’intégrations et une infrastructure utile pour exposer des fonctionnalités de langage à une variété d’outils.

Un protocole commun permet l’intégration de fonctionnalités de langage de programmation dans un outil de développement avec un minimum d’efforts en réutilisant une implémentation existante de la langue modèle de domaine. Un serveur de langue back-end peut être écrite en PHP, Python ou Java et LSP lui permet d’être facilement intégré à une variété d’outils. Le protocole fonctionne à un niveau commun d’abstraction afin qu’un outil peut offrir des services de langage enrichi sans avoir à comprendre parfaitement les nuances spécifiques au modèle de domaine sous-jacent.

## <a name="how-work-on-the-lsp-started"></a>Fonctionnement des LSP démarré

LSP a évolué au fil du temps et aujourd'hui, il est à la Version 3.0. Il a démarré lorsque le concept d’un serveur de langue a été récupéré par OmniSharp pour fournir des fonctionnalités d’édition enrichies pour c#. Au départ, OmniSharp utilisé le protocole HTTP avec une charge utile JSON et a été intégrée à plusieurs éditeurs notamment [Visual Studio Code](https://code.visualstudio.com).

En même temps, Microsoft a démarré pour travailler sur un serveur de langage TypeScript, avec l’idée de prendre en charge TypeScript dans les éditeurs de Emacs et Sublime de texte. Dans cette implémentation, un éditeur communique via stdin/stdout avec le processus de serveur TypeScript et utilise une charge utile JSON d’inspirés par le protocole du débogueur V8 pour les demandes et réponses. Le serveur TypeScript a été intégré dans le plug-in Sublime TypeScript et le Code de Visual Studio pour la modification de TypeScript enrichi.

Après l’intégration de deux serveurs de langue différente, l’équipe Visual Studio Code démarré l’exploration d’un protocole de serveur de langage commun pour les éditeurs et IDE. Un protocole commun permet à un fournisseur de langage créer un serveur de langue unique qui peut être consommé par différents IDE. Un consommateur de serveur de langage doit implémenter le côté client du protocole qu’une seule fois. Cela provoque une situation gagnant-gagnant pour le fournisseur de langage et le consommateur de langage.

Le protocole de serveur de langage a démarré avec le protocole utilisé par le serveur TypeScript, développer avec plusieurs fonctionnalités du langage inspirées par le API du langage VS Code. Le protocole est sauvegardé avec JSON-RPC d’appel de méthode distant en raison de sa simplicité et de bibliothèques existants.

La VS Code équipe prototypée protocole par l’implémentation de plusieurs serveurs de langage lint qui répondent à des demandes à lint (analyse) un fichier et renvoyer un ensemble d’erreurs et les avertissements détectés. L’objectif était de type "lint" un fichier en tant que les modifications d’utilisateurs dans un document, ce qui signifie qu’il y aura de demandes pelucheux pendant une session d’éditeur. Il avait un sens pour maintenir un serveur de configuration et en cours d’exécution afin qu’un nouveau processus pelucheux n’était pas nécessaire doit être démarrée pour chaque modification de l’utilisateur. Plusieurs serveurs lint ont été implémentés, y compris du Code Visual Studio extensions ESLint et TSLint. Ces deux serveurs lint sont à la fois implémentés dans TypeScript/JavaScript et s’exécutent sur Node.js. Ils partagent une bibliothèque qui implémente la partie client et le serveur du protocole.

## <a name="how-the-lsp-works"></a>Fonctionne des LSP

Un serveur de langage s’exécute dans son propre processus, et des outils tels que Visual Studio ou Visual Studio Code communiquent avec le serveur à l’aide du protocole de langue sur JSON-RPC. Un autre avantage de la langue de fonctionnement du serveur dans un processus est que les problèmes de performances liés à un modèle de processus unique sont évités. Le canal de transport réel peut être stdio, sockets, canaux nommés ou nœud ipc si le client et le serveur sont écrits dans Node.js.

Ci-dessous est un exemple de la façon dont un outil et un serveur de langue communiquent au cours d’une routine de session d’édition :

![diagramme de flux LSP](media/lsp-flow-diagram.png)

* **L’utilisateur ouvre un fichier (également appelé un document) dans l’outil**: l’outil avertit le serveur de la langue qu’un document est ouvert (' textDocument/didOpen »). Dès lors, la vérité sur le contenu du document n’est plus sur le système de fichiers mais conservés par l’outil dans la mémoire.

* **L’utilisateur effectue des modifications**: l’outil avertit le serveur sur la modification de document (« textDocument/didChange ») et les informations de sémantique du programme sont mis à jour par le serveur de langue. Dans ce cas, le serveur de langage analyse ces informations et avertit l’outil avec les erreurs détectées et les avertissements (« textDocument/publishDiagnostics »).

* **L’utilisateur exécute « Atteindre la définition » sur un symbole dans l’éditeur**: l’outil envoie une demande de « textDocument/définition » avec deux paramètres : (1) l’URI du document et (2) la position du texte à partir d’où la demande de définition d’atteindre a été démarrée sur le serveur. Le serveur répond avec l’URI du document et de la position de la définition du symbole dans le document.

* **L’utilisateur ferme le document (fichier)**: envoi d’une notification de ' textDocument/didClose' à partir de l’outil, qui informe le serveur de la langue que le document est maintenant n’est plus en mémoire et que le contenu actuel est maintenant à jour sur le système de fichiers.

Cet exemple illustre comment le protocole communique avec le serveur de langue au niveau des fonctionnalités de l’éditeur telles que « Atteindre la définition », « Rechercher toutes les références ». Les types de données utilisés par le protocole sont éditeur ou IDE, types de données tels que le document actuellement ouvert et la position du curseur. Les types de données ne sont pas au niveau d’un modèle de domaine langage programmation qui offre généralement les arborescences de syntaxe abstraite et les symboles de compilation (par exemple, types résolus, espaces de noms,...). Cela simplifie considérablement le protocole.

Maintenant nous allons examiner à la demande ' textDocument/définition' plus en détail. Voici les charges utiles qui vont entre l’outil client et le serveur de langage pour la demande « Atteindre la définition » dans un document de C++.

Il s’agit de la demande :

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

Il s’agit de la réponse :

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

Dans retrospect, décrivant les types de données au niveau de l’éditeur, plutôt qu’au niveau du modèle de langage de programmation est une des raisons de la réussite du protocole du serveur de langue. Il est beaucoup plus simple normaliser un document texte URI ou une position de curseur par rapport à la standardisation un symboles de compilateur et d’arborescence de syntaxe abstraite entre les différents langages de programmation.

Lorsqu’un utilisateur travaille avec différentes langues, VS Code commence en général un serveur de langue pour chaque langage de programmation. L’exemple ci-dessous montre une session où l’utilisateur travaille sur les fichiers Java et SASS.

![Java et sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Fonctionnalités

Pas de chaque serveur peut prendre en charge toutes les fonctions définies par le protocole. Par conséquent, le client et le serveur annonce son jeu de fonctionnalités prises en charge par le biais « fonctionnalités ». Par exemple, un serveur annonce qu’il puisse traiter la demande de ' textDocument/définition', mais il peut ne pas gérer la demande 'espace de travail/symbole'. De même, les clients peuvent annoncer qu’ils sont en mesure de fournir ' sur le point d’enregistrer' notifications avant l’enregistrée d’un document, afin qu’un serveur peut calculer des modifications de textuels pour mettre en forme automatiquement le document modifié.

## <a name="integrating-a-language-server"></a>Intégration d’un serveur de langue

L’intégration réelle d’un serveur de langue dans un outil spécifique n’est pas définie par le protocole de serveur de langue et le reste pour les implémenteurs de l’outil. Certains outils intègrent les serveurs de langue générique en ayant une extension qui peut démarrer et communiquer avec n’importe quel type de serveur de langue. D’autres, comme Visual Studio Code, créent une extension personnalisée par serveur, afin que l’extension est toujours en mesure de fournir des fonctionnalités de langage personnalisé.

Pour simplifier l’implémentation des serveurs de langue et des clients, des bibliothèques ou des kits de développement logiciel pour les composants client et serveur. Ces bibliothèques sont fournis pour des langues différentes. Par exemple, il est un [module de langue client npm](https://www.npmjs.com/package/vscode-languageclient) pour faciliter l’intégration d’un serveur de langue dans une extension VS Code et l’autre [module de langue serveur npm](https://www.npmjs.com/package/vscode-languageserver) pour écrire un serveur de langue à l’aide de Node.js. Il est en cours [liste](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) des bibliothèques de prise en charge.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>À l’aide du protocole de serveur de langage dans Visual Studio

* [Ajout d’une extension du protocole du serveur langue](adding-an-lsp-extension.md) -en savoir plus sur l’intégration d’un serveur de langage dans Visual Studio.
