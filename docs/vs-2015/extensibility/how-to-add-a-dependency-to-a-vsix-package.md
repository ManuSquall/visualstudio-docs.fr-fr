---
title: 'Comment : ajouter une dépendance à un package VSIX | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 997c0df133b72d69dfb4e69de53a1b77e1a0965c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697511"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Guide pratique ajouter une dépendance à un package VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez configurer un déploiement de package VSIX qui installe toutes les dépendances qui ne sont pas déjà présentes sur l’ordinateur cible. Pour ce faire, incluez les dépendances VSIX dans le fichier source. extension. vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Pour ajouter une dépendance  
  
1. Ouvrez le fichier source. extension. vsixmanifest en mode **Design** . Accédez à l’onglet **dépendances** , puis cliquez sur **nouveau**.  
  
2. Pour ajouter une extension installée : dans la boîte de dialogue **Ajouter une nouvelle dépendance** , sélectionnez **extension installée** , puis, pour le **nom**, sélectionnez une extension dans la liste.  
  
3. Pour ajouter un autre VSIX qui n’est pas installé :: dans la boîte de dialogue **Ajouter une nouvelle dépendance** , sélectionnez **fichier dans le système de fichiers** , puis utilisez le bouton **Parcourir** pour sélectionner le VSIX.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur le schéma d’extension VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Préparation d’extensions au déploiement de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
