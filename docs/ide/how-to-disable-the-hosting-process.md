---
title: Guide pratique pour désactiver le processus d’hébergement
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f7970ff97c7aec42f8798da07cf2a4a2b6c8bea8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-disable-the-hosting-process"></a>Guide pratique pour désactiver le processus d’hébergement

Les appels à certaines API peuvent être affectés quand le processus hôte est activé. Dans ces situations, il est nécessaire de désactiver le processus d’hébergement pour retourner les résultats corrects.

## <a name="to-disable-the-hosting-process"></a>Pour désactiver le processus d’hébergement

1.  Ouvrez un projet exécutable dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Les projets qui ne produisent pas de fichiers exécutables (par exemple, les projets de bibliothèque de classes ou de service) n’ont pas cette option.

2.  Dans le menu **Projet**, cliquez sur **Propriétés**.

3.  Cliquez sur l’onglet **Déboguer**.

4.  Décochez la case **Activer le processus d’hébergement Visual Studio**.

 Quand le processus d’hébergement est désactivé, plusieurs fonctionnalités de débogage sont indisponibles ou subissent une baisse des performances. Pour plus d’informations, consultez [Débogage et processus d’hébergement](../debugger/debugging-and-the-hosting-process.md).

 En général, quand le processus d’hébergement est désactivé :

-   le temps nécessaire pour commencer le débogage des applications [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] augmente ;

-   l’évaluation d’une expression au moment du design n’est pas disponible ;

-   le débogage de confiance partielle n’est pas disponible.

## <a name="see-also"></a>Voir aussi

- [Débogage et processus d’hébergement](../debugger/debugging-and-the-hosting-process.md)
- [Processus d’hébergement (vshost.exe)](../ide/hosting-process-vshost-exe.md)