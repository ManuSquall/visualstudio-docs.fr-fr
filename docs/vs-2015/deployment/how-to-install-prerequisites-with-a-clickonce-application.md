---
title: 'Comment : installer les composants requis avec une application ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18c8dd4d0bc79ac2f3af44b8b5f8dd6faacb9f45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839534"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Comment : installer les composants requis avec une application ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toutes les [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applications requièrent que la version correcte du .NET Framework soit installée sur un ordinateur avant de pouvoir être exécutées. de nombreuses applications ont également d’autres conditions préalables. Lors de la publication d’une [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application, vous pouvez choisir un ensemble de composants requis à empaqueter avec votre application. Au moment de l’installation, un contrôle est effectué pour chaque composant requis pour déterminer s’il existe déjà. Si ce n’est pas le cas, il sera installé avant l’installation de l' [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application.  
  
 Au lieu d’utiliser les composants requis pour la publication et l’empaquetage, vous pouvez également spécifier un emplacement de téléchargement pour les composants. Par exemple, plutôt que d’inclure les composants requis pour chaque application que vous publiez, vous pouvez utiliser un partage de fichiers centralisé ou un emplacement Web contenant les programmes d’installation pour tous vos composants requis. au moment de l’installation, les composants sont téléchargés et installés à partir de cet emplacement.  
  
> [!IMPORTANT]
> Vous devez ajouter des packages d’installation de composants requis à votre ordinateur de développement avant de publier votre première [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application. Pour plus d’informations, consultez [Comment : inclure des composants requis avec une application ClickOnce](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).  
  
 Les composants requis sont gérés dans la boîte de dialogue **composants requis** , accessible à partir du volet **publier** du **Concepteur de projet**.  
  
> [!NOTE]
> En plus de la liste prédéterminée des conditions préalables, vous pouvez ajouter vos propres composants à la liste. Pour plus d’informations, consultez [création de packages de programme d’amorçage](../deployment/creating-bootstrapper-packages.md).  
  
### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Pour spécifier les conditions préalables à l’installation avec une application ClickOnce  
  
1. Quand un projet est sélectionné dans **Explorateur de solutions**, dans le menu **projet** , cliquez sur **Propriétés**.  
  
2. Sélectionnez le volet **publier** .  
  
3. Cliquez sur le bouton **composants requis** pour ouvrir la boîte de dialogue **composants requis** .  
  
4. Dans la boîte de dialogue **Composants requis** , vérifiez que la case à cocher **Créer un programme d'installation des composants requis** est activée.  
  
5. Dans la liste des composants **requis** , vérifiez les composants que vous souhaitez installer, puis cliquez sur **OK**.  
  
     Les composants sélectionnés seront empaquetés et publiés en même temps que votre application.  
  
### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Pour spécifier un autre emplacement de téléchargement pour les composants requis  
  
1. Quand un projet est sélectionné dans **Explorateur de solutions**, dans le menu **projet** , cliquez sur **Propriétés**.  
  
2. Sélectionnez le volet **publier** .  
  
3. Cliquez sur le bouton **composants requis** pour ouvrir la boîte de dialogue **composants requis** .  
  
4. Dans la boîte de dialogue **Composants requis** , vérifiez que la case à cocher **Créer un programme d'installation des composants requis** est activée.  
  
5. Dans la section **spécifier l’emplacement d’installation des composants requis** , sélectionnez **Télécharger les composants requis à partir de l’emplacement suivant**.  
  
6. Sélectionnez un emplacement dans la liste déroulante, ou entrez une URL, un chemin d’accès de fichier ou un emplacement FTP, puis cliquez sur **OK.**  
  
    > [!NOTE]
    > Vous devez vous assurer que les programmes d’installation des composants spécifiés existent à l’emplacement spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Comment : publier une application ClickOnce à l'aide de l'Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
