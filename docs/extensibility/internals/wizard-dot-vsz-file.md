---
title: Assistant (. Vsz) | Microsoft Docs
description: En savoir plus sur les fichiers. vsz que l’IDE utilise pour démarrer les assistants. Les fichiers contiennent des informations sur l’Assistant à appeler et les éléments à passer à l’Assistant.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: de687dae79fa1613090fb400f73ab658ee5d66cb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900652"
---
# <a name="wizard-vsz-file"></a>Fichier Assistant (.Vsz)

L’environnement de développement intégré (IDE) utilise des fichiers. vsz pour démarrer les assistants. Ces fichiers. vsz contiennent des informations que l’IDE utilise pour déterminer l’Assistant à appeler et les informations à passer à l’Assistant.

Un fichier. vsz est une version d’un fichier texte au format .ini qui n’a aucune section. Les informations connues de l’IDE sont stockées au début du fichier. Cela fournit un lien entre l’Assistant appelé par l’IDE et les paramètres figurant dans le fichier. vsz à passer à l’IDE. Le reste du fichier fournit des paramètres qui sont spécifiques à l’Assistant et qui doivent être collectés par l’IDE et transmis à l’Assistant spécifique.

L’exemple suivant montre le contenu d’un fichier. vsz.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

Voici les parties du fichier. vsz.

|Partie|Description|
|----------|-----------------|
|VSWizard|Le premier paramètre dans le fichier est le numéro de version du format de fichier de modèle. Ce numéro de version doit être 6,0, 7,0, 7,1 ou 8,0. Les autres numéros ne peuvent pas être démarrés et provoquent une erreur de format non valide.|
|Assistant|Ce champ contient l’identificateur de programme (ProgID) OLE de l’Assistant ou une représentation sous forme de chaîne GUID du CLSID de l’Assistant qui est cocréé par l’IDE.|
|Paramètre|Ces éléments sont facultatifs. Vous pouvez en ajouter autant que nécessaire.|

Les paramètres permettent au fichier. vsz de passer des paramètres personnalisés supplémentaires à l’Assistant. Chaque valeur est passée en tant qu’élément de chaîne dans un tableau de variantes à l’Assistant. Pour plus d’informations, consultez [paramètres personnalisés](../../extensibility/internals/custom-parameters.md).

Pour ajouter un ID de paramètres régionaux par défaut à votre fichier. vsz, spécifiez `FALLBACK_LCID` = xxxx, où XXXX correspond à l’ID de paramètres régionaux, par exemple 1033 pour l’anglais. Quand le `FALLBACK_LCID` paramètre est défini, l’Assistant utilise l’ID de paramètres régionaux de secours fourni si l’ID actuel est introuvable.

## <a name="see-also"></a>Voir aussi

- [Paramètres personnalisés](../../extensibility/internals/custom-parameters.md)
- [Assistants](../../extensibility/internals/wizards.md)
- [Fichiers de description de répertoire de modèles (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
