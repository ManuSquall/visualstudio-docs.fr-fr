---
title: 'Comment : spécifier le mode d’installation en ligne ou hors connexion ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d4111ca5aee4a405a4a797dbfee14a3d4b50435f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149748"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Comment : spécifier le mode d'installation en ligne et hors connexion ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Install Mode`Pour une [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application détermine si l’application sera disponible hors connexion ou en ligne. Lorsque vous choisissez **l’application est disponible en ligne uniquement**, l’utilisateur doit avoir accès à l' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] emplacement de publication (une page Web ou un partage de fichiers) pour exécuter l’application. Lorsque vous choisissez **l’application est également disponible hors connexion**, l’application ajoute des entrées au menu **Démarrer** et à la boîte de dialogue **Ajout/suppression de programmes** . l’utilisateur peut exécuter l’application quand elle n’est pas connectée.  
  
 `Install Mode`Peut être défini sur la page **publier** du concepteur de **projets**.  
  
 **Remarque** `Install Mode` Peut également être défini à l’aide de l’Assistant Publication. Pour plus d’informations, consultez [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Pour rendre une application ClickOnce disponible en ligne uniquement  
  
1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2. Cliquez sur l'onglet **Publier**.  
  
3. Dans la zone **mode et paramètres d’installation** , cliquez sur la case d’option **l’application est disponible en ligne uniquement** .  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Pour rendre une application ClickOnce disponible en ligne ou hors connexion  
  
1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2. Cliquez sur l'onglet **Publier**.  
  
3. Dans la zone **mode et paramètres d’installation** , cliquez sur la case d’option **l’application est également disponible hors connexion** .  
  
     Une fois installée, l’application ajoute des entrées au menu **Démarrer** et à **Ajouter ou supprimer des programmes** dans le panneau de configuration.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Choix d’une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
