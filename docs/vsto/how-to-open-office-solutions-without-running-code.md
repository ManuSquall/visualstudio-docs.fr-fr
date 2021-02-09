---
title: 'Comment : ouvrir des solutions Office sans exécuter de code'
description: Découvrez comment vous pouvez ouvrir un document ou un classeur qui contient des extensions de code managé sans exécuter le code assembleur.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 99f1a01a745544e7e11e724db9c6eafacf0ca201
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876587"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Comment : ouvrir des solutions Office sans exécuter de code
  Une solution Microsoft Office créée avec des extensions de code managé s’exécute même si le paramètre de sécurité de l’application Office de l’utilisateur final est défini sur élevé. Cela est dû au fait que la sécurité du code de l’assembly .NET est gérée par l’infrastructure Microsoft .NET, et non par Microsoft Office.

 Toutefois, il peut arriver que vous souhaitiez ouvrir un document sans exécuter le code. Par exemple, le code qui s’exécute lorsque le document s’ouvre peut modifier le contenu, mais vous souhaitez mettre à jour la manière dont le document ressemble avant que le code ne le modifie. Vous pouvez également envoyer le document contenant certaines informations à l’utilisateur, et vous ne souhaitez pas que le code s’exécute et éventuellement modifier son contenu.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Il existe plusieurs façons d’ouvrir un document ou un classeur qui contient des extensions de code managé sans exécuter le code de l’assembly.

## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Pour ignorer l’assembly à l’aide de la touche Maj

- Ouvrez les documents et les classeurs à partir du menu **fichier** tout en maintenant la touche **MAJ** enfoncée pour empêcher Word et Excel de déclencher des événements d’initialisation pendant l’ouverture du document.

    > [!NOTE]
    > Si vous ouvrez un document ou un classeur à partir du volet de tâches **prise en main** , le fait de maintenir la **touche Maj** enfoncée ne contourne pas le code. En outre, maintenir la touche Maj enfoncée n’empêche pas les événements d’être déclenchés une fois que le document est ouvert.

     Cette méthode est utile si vous souhaitez ouvrir un document pour apporter des modifications sans que le code soit en cours d’exécution et modifier d’abord le document.

## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Pour ignorer un assembly en le renommant ou en le supprimant

- Si vous disposez des autorisations nécessaires sur l’ordinateur où se trouve l’assembly, vous pouvez renommer ou supprimer l’assembly afin que le document ou le classeur ne puisse pas le trouver. Une erreur se produit chaque fois que le document Office est ouvert.

     Si la solution est utilisée par plusieurs personnes, cette méthode empêche la solution de s’exécuter pour toutes. Cela peut être utile si un problème se trouve dans le code ou un serveur référencé et si vous souhaitez empêcher tous les utilisateurs de l’exécuter.

## <a name="see-also"></a>Voir aussi
- [Sécuriser les solutions Office](../vsto/securing-office-solutions.md)
- [Déployer une solution Office](../vsto/deploying-an-office-solution.md)
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
- [Manifestes d’application et de déploiement dans les solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
