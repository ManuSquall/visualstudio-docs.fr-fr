---
title: Aperçu du protocole du serveur linguistique (en anglais) Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3bd5dce3cfb7022a8abb6397dc87b418144cbe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703103"
---
# <a name="language-server-protocol"></a>Protocole de serveur de langage

## <a name="what-is-the-language-server-protocol"></a>Qu’est-ce que le protocole de serveur de langue ?

Soutenir de riches fonctionnalités d’édition comme les auto-achèvements de code source ou **Aller à la définition** pour un langage de programmation dans un éditeur ou IDE est traditionnellement très difficile et long. Habituellement, il faut écrire un modèle de domaine (un scanner, un analyseur, un contrôleur de type, un constructeur et plus) dans le langage de programmation de l’éditeur ou IDE. Par exemple, le plugin Eclipse CDT, qui fournit un support pour C / C dans l’IDE Eclipse est écrit en Java depuis l’Eclipse IDE lui-même est écrit en Java. En suivant cette approche, il s’agirait de la mise en œuvre d’un modèle de domaine C/CMD dans TypeScript pour Visual Studio Code, et d’un modèle de domaine distinct dans C pour Visual Studio.

La création de modèles de domaine spécifiques à la langue est également beaucoup plus facile si un outil de développement peut réutiliser les bibliothèques existantes spécifiques à la langue. Cependant, ces bibliothèques sont généralement mises en œuvre dans le langage de programmation lui-même (par exemple, de bons modèles de domaine C/CM sont mis en œuvre en C/CM). L’intégration d’une bibliothèque C/CMD dans un éditeur écrit dans TypeScript est techniquement possible mais difficile à faire.

### <a name="language-servers"></a>Serveurs linguistiques

Une autre approche consiste à gérer la bibliothèque dans son propre processus et à utiliser la communication interprofessionnelle pour lui parler. Les messages envoyés d’avant en arrière forment un protocole. Le protocole du serveur linguistique (LSP) est le produit de la normalisation des messages échangés entre un outil de développement et un processus de serveur de langue. L’utilisation de serveurs de langue ou de démons n’est pas une idée nouvelle ou nouvelle. Des rédacteurs comme Vim et Emacs le font depuis un certain temps pour fournir un soutien sémantique auto-achèvement. L’objectif du LSP était de simplifier ce genre d’intégrations et de fournir un cadre utile pour exposer les caractéristiques linguistiques à une variété d’outils.

Avoir un protocole commun permet l’intégration de fonctionnalités de langage de programmation dans un outil de développement avec un minimum d’agitation en réutilisant une mise en œuvre existante du modèle de domaine de la langue. Un back-end serveur de langue peut être écrit en PHP, Python, ou Java et le LSP lui permet d’être facilement intégré dans une variété d’outils. Le protocole fonctionne à un niveau commun d’abstraction afin qu’un outil puisse offrir des services linguistiques riches sans avoir besoin de bien comprendre les nuances propres au modèle de domaine sous-jacent.

## <a name="how-work-on-the-lsp-started"></a>Comment le travail sur le LSP a commencé

Le LSP a évolué au fil du temps et aujourd’hui il est à la version 3.0. Il a commencé lorsque le concept d’un serveur de langue a été repris par OmniSharp pour fournir de riches fonctionnalités d’édition pour C . Initialement, OmniSharp a utilisé le protocole HTTP avec une charge utile JSON et a été intégré dans plusieurs éditeurs, y compris [Visual Studio Code](https://code.visualstudio.com).

À peu près à la même époque, Microsoft a commencé à travailler sur un serveur de langage TypeScript, avec l’idée de prendre en charge TypeScript dans des éditeurs comme Emacs et Sublime Text. Dans cette implémentation, un éditeur communique par stdin/stdout avec le processus serveur TypeScript et utilise une charge utile JSON inspirée par le protocole de débbuggeur V8 pour les demandes et les réponses. Le serveur TypeScript a été intégré dans le plugin TypeScript Sublime et le code VS pour l’édition typeScript riche.

Après avoir intégré deux serveurs linguistiques différents, l’équipe de VS Code a commencé à explorer un protocole de serveur de langage commun pour les éditeurs et les IDE. Un protocole commun permet à un fournisseur de langues de créer un serveur linguistique unique qui peut être consommé par différents IDE. Un consommateur de serveur de langue n’a qu’à implémenter le côté client du protocole une fois. Il en résulte une situation gagnant-gagnant tant pour le fournisseur de langues que pour le consommateur de langues.

Le protocole du serveur de langue a commencé avec le protocole utilisé par le serveur TypeScript, l’élargissant avec plus de fonctionnalités linguistiques inspirées par l’API en langue de code VS. Le protocole est soutenu par JSON-RPC pour l’invocation à distance en raison de sa simplicité et des bibliothèques existantes.

L’équipe de VS Code a prototype le protocole en implémentant plusieurs serveurs de langage linter qui répondent aux demandes de lint (scanner) un fichier et de retourner un ensemble d’avertissements et d’erreurs détectés. L’objectif était de la peluche d’un fichier que l’utilisateur modifie dans un document, ce qui signifie qu’il y aura de nombreuses demandes de linting au cours d’une session d’éditeur. Il était logique de maintenir un serveur opérationnel de sorte qu’un nouveau processus de linting n’ait pas besoin d’être lancé pour chaque modification d’utilisateur. Plusieurs serveurs linter ont été implémentés, y compris les extensions ESLint et TSLint de VS Code. Ces deux serveurs linter sont tous deux implémenté dans TypeScript/JavaScript et exécutés sur Node.js. Ils partagent une bibliothèque qui implémente le client et le serveur partie du protocole.

## <a name="how-the-lsp-works"></a>Fonctionnement du LSP

Un serveur de langue fonctionne dans son propre processus, et des outils comme Visual Studio ou VS Code communiquent avec le serveur en utilisant le protocole de langue sur JSON-RPC. Un autre avantage du serveur linguistique opérant dans un processus dédié est que les problèmes de performances liés à un modèle de processus unique sont évités. Le canal de transport réel peut être stdio, prises, tuyaux nommés, ou ipc noeud si le client et le serveur sont écrits dans Node.js.

Voici un exemple pour la façon dont un outil et un serveur de langue communiquent au cours d’une session d’édition de routine :

![diagramme de flux de lsp](media/lsp-flow-diagram.png)

* **L’utilisateur ouvre un fichier (appelé document) dans l’outil**: L’outil informe le serveur de langue qu’un document est ouvert («textDocument/didOpen»). Désormais, la vérité sur le contenu du document n’est plus sur le système de fichiers mais conservée par l’outil en mémoire.

* **L’utilisateur effectue des modifications**: L’outil informe le serveur sur la modification du document («textDocument/didChange») et les informations sémantiques du programme sont mises à jour par le serveur linguistique. Dans ce cas, le serveur de langue analyse ces informations et informe l’outil avec les erreurs et les avertissements détectés («textDocument/publishDiagnostics»).

* **L’utilisateur exécute "Go to Definition" sur un symbole de l’éditeur**: L’outil envoie une demande de "textDocument/définition" avec deux paramètres: (1) le document URI et (2) la position de texte d’où la demande Go to Definition a été initiée au serveur. Le serveur répond avec le document URI et la position de la définition du symbole à l’intérieur du document.

* **L’utilisateur ferme le document (fichier)**: Une notification «textDocument/didClose» est envoyée à partir de l’outil, informant le serveur de langue que le document n’est plus en mémoire et que le contenu actuel est désormais à jour sur le système de fichiers.

Cet exemple illustre comment le protocole communique avec le serveur de langue au niveau des fonctionnalités de l’éditeur comme «Go to Definition», «Trouver toutes les références». Les types de données utilisés par le protocole sont les « types de données » de l’éditeur ou de l’IDE, comme le document texte actuellement ouvert et la position du curseur. Les types de données ne sont pas au niveau d’un modèle de domaine linguistique de programmation qui fournirait généralement des arbres syntaxes abstraits et des symboles de compilateur (par exemple, les types résolus, les espaces nominaux, ...). Cela simplifie le protocole de manière significative.

Examinons maintenant plus en détail la demande de «textedocument/définition». Vous trouverez ci-dessous les charges utiles qui vont entre l’outil client et le serveur de langue de la demande « Go to Definition » dans un document CMD.

Voici la demande :

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

Voici la réponse :

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

Rétrospectivement, décrire les types de données au niveau de l’éditeur plutôt qu’au niveau du modèle de langage de programmation est l’une des raisons du succès du protocole du serveur linguistique. Il est beaucoup plus simple de normaliser un document texte URI ou une position curseur par rapport à la normalisation d’un arbre syntaxe abstraite et des symboles compilateur à travers différents langages de programmation.

Lorsqu’un utilisateur travaille avec des langues différentes, VS Code démarre généralement un serveur linguistique pour chaque langage de programmation. L’exemple ci-dessous montre une session où l’utilisateur travaille sur les fichiers Java et SASS.

![java et sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Fonctionnalités

Tous les serveurs linguistiques ne peuvent pas prendre en charge toutes les fonctionnalités définies par le protocole. Par conséquent, le client et le serveur annonce leur fonctionnalité prise en charge définie par des «capacités». À titre d’exemple, un serveur annonce qu’il peut traiter la demande de «textDocument/définition», mais il pourrait ne pas gérer la demande de « espace de travail/symbole ». De même, les clients peuvent annoncer qu’ils sont en mesure de fournir des notifications « sur le point d’enregistrer » avant qu’un document ne soit enregistré, de sorte qu’un serveur peut calculer les modifications textuelles pour formater automatiquement le document modifié.

## <a name="integrating-a-language-server"></a>Intégration d’un serveur linguistique

L’intégration réelle d’un serveur linguistique dans un outil particulier n’est pas définie par le protocole du serveur de langue et est laissée aux implémenteurs d’outils. Certains outils intègrent des serveurs linguistiques génériquement en ayant une extension qui peut démarrer et parler à n’importe quel type de serveur de langue. D’autres, comme VS Code, créent une extension personnalisée par serveur linguistique, de sorte qu’une extension est toujours en mesure de fournir certaines fonctionnalités linguistiques personnalisées.

Pour simplifier la mise en œuvre des serveurs linguistiques et des clients, il existe des bibliothèques ou des SDK pour les parties client et serveur. Ces bibliothèques sont fournies pour différentes langues. Par exemple, il existe un [module npm client de langue](https://www.npmjs.com/package/vscode-languageclient) pour faciliter l’intégration d’un serveur de langue dans une extension de code VS et un autre module [npm serveur de langue](https://www.npmjs.com/package/vscode-languageserver) pour écrire un serveur de langue à l’aide de Node.js. Il s’agit de la [liste](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) actuelle des bibliothèques de soutien.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Utilisation du protocole de serveur de langue dans Visual Studio

* [Ajout d’une extension de protocole de serveur de langue](adding-an-lsp-extension.md) - En savoir plus sur l’intégration d’un serveur de langue dans Visual Studio.
