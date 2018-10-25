---
title: Vue d’ensemble du protocole langage serveur | Microsoft Docs
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
ms.openlocfilehash: ad0e802bd63a9d489a98eb9f216e6739e378d590
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894857"
---
# <a name="language-server-protocol"></a>Protocole de serveur de langage

## <a name="what-is-the-language-server-protocol"></a>Qu’est le protocole de serveur de langage ?

Prise en charge de riches fonctionnalités d’édition comme source code saisie automatique ou **atteindre la définition** pour un langage de programmation dans un éditeur ou l’IDE est généralement très difficile et fastidieuse. Généralement il nécessite l’écriture d’un modèle de domaine (un scanneur, un analyseur, un outil de vérification de type, un générateur et bien plus encore) dans le langage de programmation de l’éditeur ou IDE. Par exemple, le plug-in Eclipse CDT, qui fournit la prise en charge pour C/C++ dans l’IDE Eclipse est écrit en Java, car l’IDE Eclipse lui-même est écrit en Java. Selon cette approche, il signifie implémenter un modèle de domaine dans TypeScript pour Visual Studio Code C/C++ et un modèle de domaine distincts en c# pour Visual Studio.

Création de modèles de domaine spécifique à la langue est également beaucoup plus faciles si un outil de développement peut réutiliser les bibliothèques spécifiques au langage existantes. Toutefois, ces bibliothèques sont généralement implémentées dans le langage de programmation lui-même (par exemple, une bonne C/C++ domaine modèles sont implémentées en C/C++). L’intégration d’une bibliothèque C/C++ dans un éditeur écrit en TypeScript est techniquement possible mais difficile à gérer.

### <a name="language-servers"></a>Serveurs de langue

Une autre approche consiste à exécuter la bibliothèque dans son propre processus et de communication entre processus permet de communiquer avec elle. Les messages envoyés dans les deux sens forment un protocole. Le protocole de serveur de langage (LSP) est le produit suivant : standardiser les messages échangés entre un outil de développement et un processus de serveur de langage. À l’aide de serveurs de langage ou fées n’est pas une idée de nouveau ou nouvelle. Éditeurs, tels que Vim et Emacs ont été cela pendant un certain temps prendre en charge les sémantiques la saisie semi-automatique. L’objectif des LSP était de simplifier ces sortes d’intégrations et fournissent un cadre utile pour exposer des fonctionnalités de langage à un large éventail d’outils.

Un protocole commun permet l’intégration de fonctionnalités de langage de programmation dans un outil de développement avec un minimum d’efforts en réutilisant une implémentation existante de la langue modèle de domaine. Un serveur de langage back-end peut être écrit en PHP, Python ou Java et le partenaire LSP lui permet d’être facilement intégrés à un large éventail d’outils. Le protocole fonctionne à un niveau d’abstraction commun afin qu’un outil peut offrir des services de langage enrichi sans avoir à apprécier pleinement les nuances spécifiques au modèle de domaine sous-jacent.

## <a name="how-work-on-the-lsp-started"></a>Fonctionnement des LSP démarré

Le LSP a évolué au fil du temps et il est aujourd'hui à la Version 3.0. Il démarré lorsque le concept d’un serveur de langage a été récupéré par OmniSharp pour fournir des fonctionnalités d’édition riches pour c#. Initialement, OmniSharp utilisé le protocole HTTP avec une charge utile JSON et ont été intégrée dans plusieurs éditeurs notamment [Visual Studio Code](https://code.visualstudio.com).

En même temps, Microsoft commencer à travailler sur un serveur de langage TypeScript, avec l’idée de prendre en charge de TypeScript dans les éditeurs comme Emacs et Sublime Text. Dans cette implémentation, un éditeur communique via stdin/stdout avec le processus de serveur de TypeScript et utilise une inspiré par le protocole de débogueur V8 de charge utile JSON pour les demandes et réponses. Le serveur de TypeScript a été intégré dans le plug-in Sublime TypeScript et le Code de Visual Studio pour la modification de TypeScript riche.

Après avoir intégré à deux serveurs de langue différente, l’équipe Visual Studio Code démarré l’exploration d’un protocole de serveur de langage commun pour les éditeurs et différents IDE. Un protocole commun permet à un fournisseur de langage créer un serveur de langue unique qui peut être consommé par différents IDE. Un consommateur de serveur de langage a uniquement implémenter le côté client du protocole qu’une seule fois. Cela entraîne une situation gagnant-gagnant pour le fournisseur de langages et le consommateur de langage.

Le protocole de serveur de langage démarrer avec le protocole utilisé par le serveur de TypeScript, développée avec plusieurs fonctionnalités de langage inspirées par l’API de langage de Visual Studio Code. Le protocole est sauvegardé avec JSON-RPC pour l’appel distant en raison de sa simplicité et les bibliothèques existantes.

Les VS Code équipe prototypée le protocole en implémentant plusieurs serveurs de langage linter qui répondent à des demandes à lint (analyse) un fichier et renvoyer un ensemble d’erreurs et avertissements détectés. L’objectif était de lint un fichier en tant que les modifications d’utilisateurs dans un document, ce qui signifie qu’il y aura de demandes de linting pendant une session de l’éditeur. Il paraissait logique pour maintenir un serveur de configuration et en cours d’exécution afin qu’un nouveau processus de validation lint n’était pas nécessaire au démarrage de chaque modification de l’utilisateur. Plusieurs serveurs linter ont été implémentées, y compris du Code Visual Studio extensions ESLint et TSLint. Ces deux serveurs linter sont implémentées dans TypeScript/JavaScript et exécuter sur Node.js. Ils partagent une bibliothèque qui implémente la partie client et le serveur du protocole.

## <a name="how-the-lsp-works"></a>Fonctionne des LSP

Un serveur de langage s’exécute dans son propre processus et outils tels que Visual Studio ou VS Code communiquent avec le serveur à l’aide du protocole de langage sur JSON-RPC. Un autre avantage de la langue de fonctionnement du serveur dans un processus dédié est que les problèmes de performances liés à un modèle de processus unique sont évités. Le canal de transport réel peut être stdio, sockets, canaux nommés ou nœud ipc si le client et le serveur sont écrits en Node.js.

Ci-dessous est un exemple de la façon dont un outil et un serveur de langage communiquent durant une routine de session d’édition :

![diagramme de flux LSP](media/lsp-flow-diagram.png)

* **L’utilisateur ouvre un fichier (appelé un document) dans l’outil**: l’outil avertit le serveur de langage qu’un document est ouvert (' textDocument/didOpen »). Dès lors, la vérité sur le contenu du document n’est plus sur le système de fichiers mais conservée par l’outil dans la mémoire.

* **L’utilisateur apporte des modifications**: l’outil informe le serveur sur la modification de document (« textDocument/didChange ») et les informations de sémantique du programme sont mis à jour par le serveur de langage. Dans ce cas, le serveur de langage analyse ces informations et avertit l’outil avec les erreurs détectées et les avertissements (« textDocument/publishDiagnostics »).

* **L’utilisateur exécute « Atteindre la définition » sur un symbole dans l’éditeur**: l’outil envoie une demande de « textDocument/définition » avec deux paramètres : (1) l’URI de document et (2) la position du texte à partir d’où la demande de définition d’atteindre a été lancée sur le serveur. Le serveur répond avec l’URI de document et de la position de la définition du symbole à l’intérieur du document.

* **L’utilisateur ferme le document (fichier)**: envoi d’une notification de ' textDocument/didClose' à partir de l’outil, qui informe le serveur de langage qui le document est maintenant n’est plus en mémoire et que le contenu actuel est maintenant à jour sur le système de fichiers.

Cet exemple illustre la façon dont le protocole communique avec le serveur de langage au niveau des fonctionnalités de l’éditeur « Atteindre la définition », « Rechercher toutes les références ». Les types de données utilisés par le protocole sont éditeur ou IDE, types de données tels que le document actuellement ouvert et la position du curseur. Les types de données ne sont pas au niveau d’un modèle de domaine langage programmation, ce qui vous donne généralement des arborescences de syntaxe abstraite et des symboles de compilation (par exemple, types résolues, espaces de noms,...). Cela simplifie considérablement le protocole.

Maintenant nous allons examiner la demande « textDocument/définition » plus en détail. Voici les charges utiles qui vont entre l’outil client et le serveur de langage pour la demande « Atteindre la définition » dans un document de C++.

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

Rétrospectivement, décrivant les types de données au niveau de l’éditeur, plutôt qu’au niveau du modèle de langage de programmation est une des raisons de la réussite du protocole du serveur de langage. Il est beaucoup plus simple normaliser les URI de document texte ou une position de curseur par rapport à standardiser une symboles de compilateur et d’arborescence de syntaxe abstraite entre les différents langages de programmation.

Lorsqu’un utilisateur travaille avec différentes langues, VS Code démarre généralement un serveur de langage pour chaque langage de programmation. L’exemple ci-dessous montre une session où l’utilisateur travaille sur les fichiers Java et SASS.

![Java et sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Fonctionnalités

Pas de chaque serveur de langage peut prendre en charge toutes les fonctionnalités définies par le protocole. Par conséquent, le client et le serveur annonce leur jeu de fonctionnalités prises en charge par le biais « fonctionnalités ». Par exemple, un serveur annonce qu’il puisse traiter la demande de « textDocument/définition », mais il peut ne pas gérer la demande 'espace de travail/symbol'. De même, les clients peuvent annoncer qu’ils sont en mesure de fournir « sur le point d’enregistrer' notifications avant l’enregistrée d’un document, afin qu’un serveur peut calculer des modifications textuelles pour mettre en forme automatiquement le document modifié.

## <a name="integrating-a-language-server"></a>Intégration d’un serveur de langage

L’intégration réelle d’un serveur de langage à un outil particulier n’est pas définie par le protocole de serveur de langage et le reste pour les implémenteurs de l’outil. Certains outils intègrent les serveurs de langage de façon générique en ayant une extension qui peut commencer et communiquer avec n’importe quel type de serveur de langage. D’autres, tels que Visual Studio Code, créez une extension personnalisée par serveur de langage, afin qu’une extension est toujours en mesure de fournir des fonctionnalités de langue personnalisé.

Pour simplifier l’implémentation de serveurs de langage et les clients, il existe les bibliothèques ou les kits de développement logiciel pour les parties client et serveur. Ces bibliothèques sont fournis pour des langues différentes. Par exemple, il existe un [module npm de client language](https://www.npmjs.com/package/vscode-languageclient) pour faciliter l’intégration d’un serveur de langage dans une extension VS Code et l’autre [module npm de serveur language](https://www.npmjs.com/package/vscode-languageserver) pour écrire une langue serveur à l’aide de Node.js. Il s’agit d’actuel [liste](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) des bibliothèques de prise en charge.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>L’aide du protocole de serveur de langage dans Visual Studio

* [Ajout d’une extension du protocole de serveur de langage](adding-an-lsp-extension.md) -en savoir plus sur l’intégration d’un serveur de langage dans Visual Studio.
