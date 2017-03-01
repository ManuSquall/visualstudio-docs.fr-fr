---
title: Assistant (. Fichier vsz) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f1dc3ff7964ea5290ffe926ef75773a7210b6449
ms.lasthandoff: 02/22/2017

---
# <a name="wizard-vsz-file"></a>Assistant (. Fichier vsz)
L’environnement de développement intégré (IDE) utilise des fichiers .vsz pour démarrer des Assistants. Ces fichiers .vsz contiennent des informations utilisées par l’IDE pour déterminer l’Assistant à appeler et les informations à passer à l’Assistant.  
  
 Un fichier .vsz est une version d’un fichier texte au format .ini a pas de sections. Informations connues de l’IDE se trouve au début du fichier. Cela fournit un lien entre l’Assistant qui appelle l’IDE et les paramètres qui se trouvent dans le fichier .vsz à passer à l’IDE. Le reste du fichier fournit des paramètres qui sont spécifiques à l’Assistant et qui doivent être collectées par l’IDE et passé à l’Assistant spécifique.  
  
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
|VSWizard|Le premier paramètre dans le fichier est le numéro de version du format de fichier modèle. Ce numéro de version doit être 6.0, 7.0, 7.1 ou 8.0. Autres nombres ne peut pas être démarré et provoquer une erreur de Format non valide.|  
|Assistant|Ce champ contient le ProgID OLE de l’Assistant, ou une représentation de chaîne GUID du CLSID de l’Assistant qui est co-créé par l’IDE.|  
|Param|Ces parties sont facultatives. Vous pouvez ajouter que nécessaire.|  
  
 Les paramètres permettent au fichier .vsz de passer des paramètres personnalisés supplémentaires à l’Assistant. Chaque valeur est passée comme un élément de chaîne dans un tableau de Variant à l’Assistant. Pour plus d’informations, consultez [personnalisé paramètres](../../extensibility/internals/custom-parameters.md). Pour plus d’informations sur l’utilisation d’un fichier .vsz dans le développement d’Assistants personnalisés, consultez [. Fichiers vsz (contrôle de projet)](/visual-cpp/ide/dot-vsz-file-project-control)  
  
 Pour ajouter un ID de paramètres régionaux par défaut dans votre fichier .vsz, spécifiez `FALLBACK_LCID`= xxxx, où xxxx est l’ID de paramètres régionaux, par exemple, 1033 pour l’anglais. Lorsque `FALLBACK_LCID` est défini, l’Assistant utilise l’ID de paramètres régionaux de base fourni si l’ID actuel est introuvable.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres personnalisés](../../extensibility/internals/custom-parameters.md)   
 [Assistants](../../extensibility/internals/wizards.md)   
 [Description du modèle active (. Fichiers VSDir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
