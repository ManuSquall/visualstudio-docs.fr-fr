---
title: Processus d’hébergement (vshost.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a998246f514f13a575f6a7fef850f9f705f92553
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645534"
---
# <a name="hosting-process-vshostexe"></a>Processus d'hébergement (vshost.exe)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le processus d’hébergement est une fonctionnalité de Visual Studio qui améliore les performances de débogage et permet le débogage de confiance partielle et l’évaluation d’une expression au moment du design. Les fichiers du processus d’hébergement contiennent vshost dans leur nom et sont placés dans le dossier de sortie de votre projet. Pour plus d’informations, consultez [Débogage et processus d’hébergement](../debugger/debugging-and-the-hosting-process.md).

> [!NOTE]
> Les fichiers du processus d’hébergement (.vshost.exe) sont utilisés par Visual Studio et ne doivent pas être exécutés directement ou déployés avec votre application.

## <a name="improved-debugging-performance"></a>Amélioration des performances de débogage
 Le processus d’hébergement crée un domaine d’application et associe le débogueur à l’application. La réalisation de ces tâches peut introduire un délai notable entre le démarrage du débogage et le début de l’exécution de l’application. Le processus d’hébergement permet d’améliorer les performances en créant le domaine d’application et en associant le débogueur en arrière-plan, ainsi qu’en enregistrant le domaine d’application et l’état du débogueur entre les exécutions de l’application. Pour plus d’informations sur les domaines d’application, consultez [Domaines d’application](https://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8).

## <a name="partial-trust-debugging"></a>Débogage de confiance partielle
 Vous pouvez spécifier une application en tant qu’application de confiance partielle dans la [page Sécurité](../ide/reference/security-page-project-designer.md) du **Concepteur de projets**. Le débogage d’une application de confiance partielle nécessite une initialisation spéciale du domaine d’application. Cette initialisation est assurée par le processus d’hébergement.

## <a name="design-time-expression-evaluation"></a>Évaluation de l’expression au moment du design
 L’évaluation de l’expression au moment du design vous permet de tester le code à partir de la fenêtre **Exécution** sans devoir exécuter l’application. Le processus d’hébergement exécute ce code pendant l’évaluation de l’expression au moment du design. Pour plus d’informations, consultez [fenêtre exécution](../ide/reference/immediate-window.md).

## <a name="see-also"></a>Voir aussi
 [Débogage et processus d’hébergement](../debugger/debugging-and-the-hosting-process.md) [Comment : désactiver les](../ide/how-to-disable-the-hosting-process.md) [domaines d’application](https://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8) de la [fenêtre exécution](../ide/reference/immediate-window.md) du processus d’hébergement
