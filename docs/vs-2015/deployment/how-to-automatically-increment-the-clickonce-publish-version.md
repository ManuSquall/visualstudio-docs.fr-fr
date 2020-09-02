---
title: 'Comment : incrémenter automatiquement la version de publication ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 50faf70e8eda6ef7ab01201102540729497eb87b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683921"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Comment : incrémenter automatiquement la version de publication ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lors de la publication d’une [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application, la modification de la `Publish Version` propriété entraîne la publication de l’application en tant que mise à jour. Par défaut, Visual Studio incrémente automatiquement le `Revision` numéro de `Publish Version` chaque fois que vous publiez l’application.  
  
 Vous pouvez désactiver ce comportement sur la page **publier** du **Concepteur de projets**.  
  
> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour modifier vos paramètres, choisissez **Paramètres d'importation et d'exportation** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>Pour désactiver l’incrémentation automatique de la version de publication  
  
1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2. Cliquez sur l'onglet **Publier**.  
  
3. Dans la section **version de publication** , désactivez la case à cocher **incrémenter automatiquement la révision avec chaque version** .  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : définir la version de publication ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Comment : publier une application ClickOnce à l'aide de l'Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
