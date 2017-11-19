---
title: "Comment : ajouter une dépendance à un Package VSIX | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d3f3b54e19d8418f35a733b73ea0616b53bd42ce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Comment : ajouter une dépendance à un Package VSIX
Vous pouvez configurer un déploiement de package VSIX qui installe les dépendances qui ne sont pas déjà présents sur l’ordinateur cible. Pour ce faire, inclure les dépendances VSIX dans le fichier source.extension.vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Pour ajouter une dépendance  
  
1.  Ouvrez le fichier source.extension.vsixmanifest dans le **conception** vue. Accédez à la **dépendances** onglet et cliquez sur **nouveau**.  
  
2.  Pour ajouter une extension installée : dans le **ajouter une nouvelle dépendance** boîte de dialogue, sélectionnez **extension installée** , puis, pour le **nom**, sélectionnez une extension dans la liste.  
  
3.  Pour ajouter une autre extension VSIX qui n’est pas installé : : dans le **ajouter une nouvelle dépendance** boîte de dialogue, sélectionnez **fichier sur le système de fichiers** , puis utilisez le **Parcourir** pour sélectionner l’extension VSIX.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de schéma 1.0 Extension VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomie d’un Package VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Préparation d’extensions pour le déploiement de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)