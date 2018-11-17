---
title: Assistant (. Fichier vsz) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 428a2faf85180b9239f128dde5a9dadca04139af
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786433"
---
# <a name="wizard-vsz-file"></a>Fichier Assistant (.Vsz)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

L’environnement de développement intégré (IDE) utilise des fichiers .vsz pour démarrer des Assistants. Ces fichiers .vsz contiennent des informations que l’IDE utilise pour déterminer quel Assistant à appeler et les informations à transmettre à l’Assistant.  
  
 Un fichier .vsz est une version d’un fichier texte au format .ini qui l’a pas de sections. Informations connues à l’IDE sont stockées au début du fichier. Cela fournit un lien entre l’Assistant qui appelle l’IDE et les paramètres qui se trouvent dans le fichier .vsz à passer à l’IDE. Le reste du fichier fournit des paramètres qui sont spécifiques à l’Assistant et qui doivent être collectées par l’IDE et transmis à l’Assistant spécifique.  
  
 L’exemple suivant montre le contenu d’un fichier .vsz.  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 Voici les parties dans le fichier .vsz.  
  
|Élément|Description|  
|----------|-----------------|  
|VSWizard|Le premier paramètre dans le fichier est le numéro de version du format de fichier de modèle. Ce numéro de version doit être 6.0, 7.0, 7.1 ou 8.0. Autres nombres ne peut pas être démarrée et provoquer une erreur de Format non valide.|  
|Assistant|Ce champ contient le ProgID OLE de l’Assistant, ou vous pouvez également une représentation de chaîne GUID du CLSID de l’Assistant qui est co-créé par l’IDE.|  
|Param|Ces parties sont facultatives. Vous pouvez ajouter autant que nécessaire.|  
  
 Les paramètres permettent au fichier .vsz de passer des paramètres personnalisés supplémentaires à l’Assistant. Chaque valeur est passée en tant qu’élément de chaîne dans un tableau de Variant à l’Assistant. Pour plus d’informations, consultez [personnalisé paramètres](../../extensibility/internals/custom-parameters.md). Pour plus d’informations sur l’utilisation d’un fichier .vsz dans le développement d’Assistants personnalisés, consultez [. Fichier vsz (contrôle de projet)](http://msdn.microsoft.com/library/b8678fee-6795-46d1-9338-48b22d5e9207)  
  
 Pour ajouter un ID de paramètres régionaux par défaut à votre fichier .vsz, spécifiez `FALLBACK_LCID`= xxxx, où xxxx correspond à l’ID de paramètres régionaux, par exemple, 1033 pour l’anglais. Lorsque `FALLBACK_LCID` paramètre est défini, l’Assistant utilise l’ID de paramètres régionaux de base fourni si l’ID actuel est introuvable.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres personnalisés](../../extensibility/internals/custom-parameters.md)   
 [Assistants](../../extensibility/internals/wizards.md)   
 [Fichiers de description de répertoire de modèles (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

