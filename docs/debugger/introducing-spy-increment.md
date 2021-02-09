---
title: Présentation de Spy + + | Microsoft Docs
description: En savoir plus sur l’outil de débogage Spy + +. Afficher une arborescence graphique des relations entre les objets système. Obtenir les propriétés des fenêtres, threads, processus ou messages sélectionnés.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Spy++
ms.assetid: 733b514b-63a9-402d-89aa-4f0416766655
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eefc69d7dbd7d05eaadc3e9fe8976c0ff03c9a30
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910020"
---
# <a name="introducing-spy"></a>Présentation de Spy++
Spy++ vous permet d’effectuer les tâches suivantes :

- Afficher une arborescence graphique des relations entre les objets système. Il s’agit notamment des [processus](../debugger/processes-view.md), [threads](../debugger/threads-view.md)et [fenêtres](../debugger/windows-view.md).

- Rechercher des [fenêtres](../debugger/how-to-search-for-a-window-in-windows-view.md), [threads](../debugger/how-to-search-for-a-thread-in-threads-view.md), [processus](../debugger/how-to-search-for-a-process-in-processes-view.md), ou [messages](../debugger/how-to-search-for-a-message-in-messages-view.md)spécifiés.

- Afficher les propriétés des [fenêtres](../debugger/how-to-display-window-properties.md), [threads](../debugger/how-to-display-thread-properties.md), [processus](../debugger/how-to-display-process-properties.md)ou [messages](../debugger/how-to-display-message-properties.md)sélectionnés.

- Sélectionne une fenêtre, un thread, un processus ou un message directement dans la vue.

- Utilisez l’ [Outil Recherche](../debugger/how-to-use-the-finder-tool.md) pour sélectionner une fenêtre grâce au positionnement du pointeur de la souris.

- Définissez l' [option message](../debugger/how-to-open-messages-view-from-find-window.md) à l’aide de paramètres de sélection de journal des messages complexes.

  Spy++ propose une barre d’outils et des liens hypertexte pour vous aider à travailler plus rapidement. Il offre également une commande **Actualiser** pour mettre à jour la vue active, un **Outil Recherche de fenêtres** pour simplifier l’espionnage, et une boîte de dialogue **Police** pour personnaliser les fenêtres d’affichage. En outre, Spy++ vous permet d’enregistrer et de restaurer les préférences de l’utilisateur.

  Dans plusieurs fenêtres Spy++, vous pouvez cliquer avec le bouton droit pour afficher un menu contextuel de commandes fréquemment utilisées. Les commandes affichées dépendent de l’emplacement du pointeur. Par exemple, si vous cliquez avec le bouton droit sur une entrée dans la vue Fenêtre et que la fenêtre sélectionnée est visible, un clic sur **Surbrillance** dans le menu contextuel fait clignoter la bordure de la fenêtre sélectionnée pour que vous puissiez l’identifier facilement.

> [!NOTE]
> Il existe deux autres utilitaires qui ressemblent à Spy++ : PView, qui affiche des détails sur les processus et les threads, et DDESPY. EXE, qui vous permet d’analyser les messages DDE (Dynamic Data Exchange).

## <a name="64-bit-operating-systems"></a>Systèmes d’exploitation 64 bits
 Il existe deux versions de Spy++. La première, nommée Spy++ (spyxx.exe), est conçue pour afficher les messages envoyés à une fenêtre qui s’exécute dans un processus 32 bits. Par exemple, Visual Studio s’exécute dans un processus 32 bits. Ainsi, vous pouvez utiliser Spy++ pour afficher les messages envoyés à l’ **Explorateur de solutions**. Étant donné que la configuration par défaut pour la plupart des builds dans Visual Studio doit s’exécuter dans un processus 32 bits, cette première version de Spy + + est celle qui est disponible dans le menu **Outils** de Visual Studio, si [des composants requis sont installés](../debugger/how-to-start-spy-increment.md).

 La deuxième version, nommée Spy++ (64 bits) (spyxx_amd64.exe), est conçue pour afficher les messages envoyés à une fenêtre qui s’exécute dans un processus 64 bits. Par exemple, sur un système d’exploitation 64 bits, le Bloc-notes s’exécute dans un processus 64 bits. Ainsi, vous pouvez utiliser Spy++ (64 bits) pour afficher les messages envoyés au Bloc-notes. Spy++ (64 bits) se trouve généralement dans

 ..\\*Visual Studio installation folder*\Common7\Tools\spyxx_amd64.exe.

 Vous pouvez exécuter l’une ou l’autre version de Spy++ directement à partir de la ligne de commande.

> [!NOTE]
> Bien que le nom de fichier Spy++ (64 bits) contienne « amd », il s’exécute sur n’importe quel système d’exploitation Windows x64.

## <a name="see-also"></a>Voir aussi
- [Comment : démarrer Spy++](../debugger/how-to-start-spy-increment.md)
- [Utiliser Spy++](../debugger/using-spy-increment.md)
- [Vues Spy++](../debugger/spy-increment-views.md)
- [Référence Spy++](../debugger/spy-increment-reference.md)