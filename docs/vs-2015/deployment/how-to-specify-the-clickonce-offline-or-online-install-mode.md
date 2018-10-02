---
title: 'Comment : spécifier le ClickOnce en mode hors connexion ou en Mode d’installation en ligne | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: 7f277966070e142ebc24d70acfcf4bf5502f419a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502374"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Comment : spécifier le mode d'installation en ligne et hors connexion ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : spécifier le ClickOnce hors connexion ou installer le Mode en ligne](https://docs.microsoft.com/visualstudio/deployment/how-to-specify-the-clickonce-offline-or-online-install-mode).  
  
Le `Install Mode` pour un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application détermine si l’application sera disponible en ligne ou hors connexion. Lorsque vous choisissez **l’application est disponible en ligne uniquement**, l’utilisateur doit avoir accès à la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] emplacement (une page Web ou un partage de fichiers) pour exécuter l’application de publication. Lorsque vous choisissez **l’application est également disponible hors connexion**, l’application ajoute des entrées à la **Démarrer** menu et le **Ajout / Suppression de programmes** boîte de dialogue ; l’utilisateur est possibilité d’exécuter l’application lorsqu’ils ne sont pas connectés.  
  
 Le `Install Mode` peuvent être définies sur le **publier** page de la **Concepteur de projet**.  
  
 **Remarque** le `Install Mode` peut également être définie à l’aide de l’Assistant Publication. Pour plus d’informations, consultez [Comment : publier une Application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Pour rendre une application ClickOnce disponible en ligne uniquement  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Dans le **installer le Mode et paramètres** zone, cliquez sur le **l’application est disponible en ligne uniquement** case d’option.  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Pour rendre une application ClickOnce disponible en ligne ou hors connexion  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Dans le **installer le Mode et paramètres** zone, cliquez sur le **l’application est également disponible hors connexion** case d’option.  
  
     Lors de l’installation, l’application ajoute des entrées à la **Démarrer** menu et **Ajout / Suppression de programmes** dans le panneau de configuration.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Choix d’une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)



