---
title: 'Procédure : Ajouter une dépendance à un Package VSIX | Microsoft Docs'
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697511"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Procédure : Ajouter une dépendance à un package VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez configurer un déploiement de package VSIX qui installe les dépendances qui ne sont pas déjà présents sur l’ordinateur cible. Pour ce faire, inclure les dépendances VSIX dans le fichier source.extension.vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Pour ajouter une dépendance  
  
1. Ouvrez le fichier source.extension.vsixmanifest dans le **conception** vue. Accédez à la **dépendances** onglet et cliquez sur **New**.  
  
2. Pour ajouter une extension installée : dans le **ajouter une nouvelle dépendance** boîte de dialogue, sélectionnez **installé extension** , puis, pour le **nom**, sélectionnez une extension dans la liste.  
  
3. Pour ajouter une autre extension VSIX qui n’est pas installé : : dans le **ajouter une nouvelle dépendance** boîte de dialogue, sélectionnez **fichier sur le système de fichiers** , puis utilisez le **Parcourir** bouton pour sélectionner l’extension VSIX.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma 1.0 Extension VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomie d’un Package VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Préparation d’extensions pour le déploiement de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
