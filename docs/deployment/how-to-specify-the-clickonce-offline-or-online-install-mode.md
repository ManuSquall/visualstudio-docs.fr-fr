---
title: 'Comment : spécifier le ClickOnce en mode hors connexion ou en Mode d’installation en ligne | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1515d9b9b12d92f7189c1dda59659d6ea1c03d5
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080171"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Comment : spécifier le ClickOnce en mode hors connexion ou en mode d’installation en ligne
Le `Install Mode` pour un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application détermine si l’application sera disponible en ligne ou hors connexion. Lorsque vous choisissez **l’application est disponible en ligne uniquement**, l’utilisateur doit avoir accès à la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] emplacement (une page Web ou un partage de fichiers) pour exécuter l’application de publication. Lorsque vous choisissez **l’application est également disponible hors connexion**, l’application ajoute des entrées à la **Démarrer** menu et le **Ajout / Suppression de programmes** boîte de dialogue ; l’utilisateur est possibilité d’exécuter l’application lorsqu’ils ne sont pas connectés.  
  
 Le `Install Mode` peuvent être définies sur le **publier** page de la **Concepteur de projet**.  
  
 **Remarque** le `Install Mode` peut également être définie à l’aide de l’Assistant Publication. Pour plus d’informations, consultez [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
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
 [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Choisissez une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)