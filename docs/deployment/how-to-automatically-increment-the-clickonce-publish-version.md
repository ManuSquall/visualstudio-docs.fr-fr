---
title: 'Comment : incrémenter automatiquement la publication ClickOnce Version | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: beada30e45ce2d46500654bca5051bd51db02d66
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151962"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Comment : incrémenter automatiquement la publication ClickOnce version
Lors de la publication une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application, en modifiant le `Publish Version` propriété entraîne l’application à publier une mise à jour. Par défaut, Visual Studio incrémente automatiquement le `Revision` numéro de la `Publish Version` chaque fois que vous publiez l’application.  
  
 Vous pouvez désactiver ce comportement sur le **publier** page de la **Concepteur de projet**.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>Pour désactiver la version de publication à incrémentation automatique  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Dans le **Publish Version** section, désactivez le **incrémenter automatiquement la révision avec chaque version** case à cocher.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : définir la publication ClickOnce version](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)