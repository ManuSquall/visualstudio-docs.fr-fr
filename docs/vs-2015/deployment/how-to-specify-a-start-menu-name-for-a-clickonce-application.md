---
title: 'Comment : spécifier un nom de menu Démarrer pour une application ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 30bb4050399bf7a6d9120f7e5454b26ce505af35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149763"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Comment : spécifier un nom de menu Démarrer pour une application ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsqu’une [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application est installée pour une utilisation en ligne et hors connexion, une entrée est ajoutée au menu **Démarrer** et à la liste **Ajouter ou supprimer des programmes** . Par défaut, le nom complet est le même que le nom de l’assembly d’application, mais vous pouvez modifier le nom complet en définissant le **nom du produit** dans la boîte de dialogue **options de publication** .  
  
 Le **nom du produit** s’affiche sur la page publish.htm ; pour une application hors connexion installée, il s’agit du nom de l’entrée dans le menu **Démarrer** , et il s’agit également du nom qui s’affiche dans **Ajout/suppression de programmes**.  
  
 Le nom de l' **éditeur** apparaît sur la page publish.htm au-dessus du **nom du produit**, et pour une application hors connexion installée, il s’agit également du nom du dossier qui contient l’icône de l’application dans le menu **Démarrer** .  
  
 Vous pouvez définir les **Propriétés nom du produit** et nom de l' **éditeur** dans la boîte de dialogue **options de publication** , disponible sur la page **publier** du concepteur de **projets**.  
  
### <a name="to-specify-a-start-menu-name"></a>Pour spécifier un nom de menu Démarrer  
  
1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2. Cliquez sur l'onglet **Publier**.  
  
3. Cliquez sur le bouton **options** pour ouvrir la boîte de dialogue **options de publication** .  
  
4. Cliquez sur **Description**.  
  
5. Dans la boîte de dialogue **options de publication** , entrez le nom à afficher dans **nom du produit**.  
  
6. Si vous le souhaitez, vous pouvez entrer un nom d’éditeur dans nom de l' **éditeur**.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Comment : publier une application ClickOnce à l'aide de l'Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
