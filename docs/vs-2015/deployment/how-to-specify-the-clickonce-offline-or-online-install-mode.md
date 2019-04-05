---
title: 'Procédure : Spécifier le ClickOnce en mode hors connexion ou en Mode d’installation en ligne | Microsoft Docs'
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
ms.openlocfilehash: 0e16c3b921c8ecd2c4c944b60cb5541eac49463e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951535"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Procédure : Spécifier le mode d’installation en ligne ou hors connexion de ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le `Install Mode` pour un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application détermine si l’application sera disponible en ligne ou hors connexion. Lorsque vous choisissez **l’application est disponible en ligne uniquement**, l’utilisateur doit avoir accès à la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] emplacement (une page Web ou un partage de fichiers) pour exécuter l’application de publication. Lorsque vous choisissez **l’application est également disponible hors connexion**, l’application ajoute des entrées à la **Démarrer** menu et le **Ajout / Suppression de programmes** boîte de dialogue ; l’utilisateur est possibilité d’exécuter l’application lorsqu’ils ne sont pas connectés.  
  
 Le `Install Mode` peuvent être définies sur le **publier** page de la **Concepteur de projet**.  
  
 **Remarque** le `Install Mode` peut également être définie à l’aide de l’Assistant Publication. Pour plus d'informations, voir [Procédure : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Pour rendre une application ClickOnce disponible en ligne uniquement  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur l’onglet **Publier**.  
  
3.  Dans le **installer le Mode et paramètres** zone, cliquez sur le **l’application est disponible en ligne uniquement** case d’option.  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Pour rendre une application ClickOnce disponible en ligne ou hors connexion  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur l’onglet **Publier**.  
  
3.  Dans le **installer le Mode et paramètres** zone, cliquez sur le **l’application est également disponible hors connexion** case d’option.  
  
     Lors de l’installation, l’application ajoute des entrées à la **Démarrer** menu et **Ajout / Suppression de programmes** dans le panneau de configuration.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Guide pratique pour Publier une Application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Choix d’une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
