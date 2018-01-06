---
title: "Comment : incrémenter ClickOnce publier automatiquement une Version | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 2e1399795400d52543b92cb13635a8485b160f22
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Comment : incrémenter automatiquement la version de publication ClickOnce
Lorsque vous publiez un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application, la modification la `Publish Version` propriété entraîne l’application à publier en tant qu’une mise à jour. Par défaut, Visual Studio incrémente automatiquement le `Revision` numéro de la `Publish Version` chaque fois que vous publiez l’application.  
  
 Vous pouvez désactiver ce comportement sur le **publier** page de la **Concepteur de projet**.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>Pour désactiver l’incrémentation automatique de la Version de publication  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Dans le **Publish Version** section, désactivez le **incrémenter automatiquement la révision avec chaque version** case à cocher.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour définir la version de publication ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)