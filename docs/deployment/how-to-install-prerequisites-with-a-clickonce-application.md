---
title: "Comment : installer les composants requis avec une Application ClickOnce | Documents Microsoft"
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
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
caps.latest.revision: "13"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 83458b627949cda5f918ec06a5f84bd9697ba6d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Comment : installer les composants requis avec une application ClickOnce
Tous les [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applications nécessitent que la version correcte du .NET Framework est installée sur un ordinateur avant de pouvoir exécuter ; les autres conditions préalables également de nombreuses applications ont. Lorsque vous publiez un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application, vous pouvez choisir un ensemble de composants requis pour être empaqueté avec votre application. Au moment de l’installation, une vérification sera effectuée pour chaque composant requis déterminer s’il existe déjà ; Si elle ne sera pas installé avant d’installer le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application.  
  
 Au lieu d’empaquetage et la publication des composants requis, vous pouvez également spécifier un emplacement de téléchargement pour les composants. Par exemple, au lieu d’inclure les composants requis avec chaque application que vous publiez, vous pouvez utiliser un partage de fichiers centralisé ou un emplacement Web qui contient les programmes d’installation pour tous vos composants requis, au moment de l’installation, les composants seront téléchargés et installer à partir de cet emplacement.  
  
> [!IMPORTANT]
>  Vous devez ajouter des packages de programme d’installation préalable sur votre ordinateur de développement avant de publier votre premier [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application. Pour plus d’informations, consultez [Comment : inclure les composants requis avec une Application ClickOnce](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).  
  
 Les composants requis sont gérés dans le **conditions préalables** boîte de dialogue, accessible à partir de la **publier** volet de la **Concepteur de projet**.  
  
> [!NOTE]
>  Outre la liste prédéterminée des composants requis, vous pouvez ajouter vos propres composants à la liste. Pour plus d’informations, consultez [création de Packages de programme d’amorçage](../deployment/creating-bootstrapper-packages.md).  
  
### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Pour spécifier les conditions requises pour installer avec une application ClickOnce  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Sélectionnez le **publier** volet.  
  
3.  Cliquez sur le **conditions préalables** bouton pour ouvrir la **conditions préalables** boîte de dialogue.  
  
4.  Dans la boîte de dialogue **Composants requis** , vérifiez que la case à cocher **Créer un programme d'installation des composants requis** est activée.  
  
5.  Dans le **conditions préalables** liste, vérifiez les composants que vous souhaitez installer, puis cliquez sur **OK**.  
  
     Les composants sélectionnés sont empaquetées et publiées avec votre application.  
  
### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Pour spécifier un autre emplacement de téléchargement pour les composants requis  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Sélectionnez le **publier** volet.  
  
3.  Cliquez sur le **conditions préalables** bouton pour ouvrir la **conditions préalables** boîte de dialogue.  
  
4.  Dans la boîte de dialogue **Composants requis** , vérifiez que la case à cocher **Créer un programme d'installation des composants requis** est activée.  
  
5.  Dans le **spécifier l’emplacement d’installation des composants requis** section, sélectionnez **télécharger les composants requis depuis l’emplacement suivant**.  
  
6.  Sélectionnez un emplacement dans la liste déroulante, ou entrez une URL, un chemin d’accès de fichier ou un emplacement FTP, puis cliquez sur **OK.**  
  
    > [!NOTE]
    >  Il se peut que vous devez vous assurer que les programmes d’installation pour les composants spécifiés existent à l’emplacement spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)