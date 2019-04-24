---
title: 'Procédure : Installer les composants requis avec une Application ClickOnce | Microsoft Docs'
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
ms.openlocfilehash: 04f6c78f3733bbc8aab3aec5811f1eb643ecca4e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056612"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Procédure : Installer des prérequis avec une application ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tous les [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] applications requièrent que la version correcte du .NET Framework est installée sur un ordinateur avant de pouvoir exécuter ; de nombreuses applications ont également autres conditions préalables requises. Lorsque vous publiez un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application, vous pouvez choisir un ensemble de composants requis à empaqueter avec votre application. Au moment de l’installation, une vérification sera effectuée pour chaque composant requis déterminer s’il existe déjà ; Si pas il sera installé avant d’installer le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application.  
  
 Au lieu d’empaquetage et publication des conditions préalables, vous pouvez également spécifier un emplacement de téléchargement pour les composants. Par exemple, au lieu d’inclure les composants requis avec chaque application que vous publiez, vous pouvez utiliser un partage de fichiers centralisé ou un emplacement Web qui contient les programmes d’installation pour tous vos composants requis, au moment de l’installation, les composants seront téléchargés et installer à partir de cet emplacement.  
  
> [!IMPORTANT]
>  Vous devez ajouter des packages de programme d’installation préalable sur votre ordinateur de développement avant de publier votre premier [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application. Pour plus d'informations, voir [Procédure : Inclure des prérequis dans une application ClickOnce](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).  
  
 Conditions préalables sont gérés dans le **prérequis** boîte de dialogue, accessible à partir de la **publier** volet de la **Concepteur de projets**.  
  
> [!NOTE]
>  Outre la liste prédéterminée des conditions préalables, vous pouvez ajouter vos propres composants à la liste. Pour plus d’informations, consultez [création de Packages de programme d’amorçage](../deployment/creating-bootstrapper-packages.md).  
  
### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Pour spécifier les composants requis à installer avec une application ClickOnce  
  
1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2. Sélectionnez le **publier** volet.  
  
3. Cliquez sur le **prérequis** bouton pour ouvrir la **conditions préalables** boîte de dialogue.  
  
4. Dans la boîte de dialogue **Composants requis** , vérifiez que la case à cocher **Créer un programme d'installation des composants requis** est activée.  
  
5. Dans le **prérequis** liste, vérifiez les composants que vous souhaitez installer, puis cliquez sur **OK**.  
  
     Les composants sélectionnés seront empaquetés et publiés en même temps que votre application.  
  
### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Pour spécifier un autre emplacement de téléchargement pour les composants requis  
  
1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2. Sélectionnez le **publier** volet.  
  
3. Cliquez sur le **prérequis** bouton pour ouvrir la **conditions préalables** boîte de dialogue.  
  
4. Dans la boîte de dialogue **Composants requis** , vérifiez que la case à cocher **Créer un programme d'installation des composants requis** est activée.  
  
5. Dans le **spécifier l’emplacement d’installation des composants requis** section, sélectionnez **télécharger les composants requis depuis l’emplacement suivant**.  
  
6. Sélectionnez un emplacement dans la liste déroulante, ou entrez une URL, un chemin d’accès de fichier ou un emplacement FTP, puis cliquez sur **OK.**  
  
    > [!NOTE]
    >  Il se peut que vous devez vous assurer que les programmes d’installation pour les composants spécifiés existent à l’emplacement spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
