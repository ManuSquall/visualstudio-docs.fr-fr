---
title: Assistant (. Vsz) Fichier (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0fedf409c0ca320c054ddf1cc16318d08d25463a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703312"
---
# <a name="wizard-vsz-file"></a>Fichier Assistant (.Vsz)

L’environnement de développement intégré (IDE) utilise des fichiers .vsz pour démarrer les assistants. Ces fichiers .vsz contiennent des informations que l’IDE utilise pour déterminer quel assistant appeler et quelles informations transmettre à l’assistant.

Un fichier .vsz est une version d’un fichier texte .ini-formaté qui n’a pas de sections. Les informations connues de l’IDE sont stockées au début du fichier. Cela fournit un lien entre l’assistant que l’IDE appelle et les paramètres qui sont dans le fichier .vsz à passer à l’IDE. Le reste du fichier fournit des paramètres spécifiques à l’assistant et qui doivent être collectés par l’IDE et transmis à l’assistant spécifique.

L’exemple suivant montre le contenu d’un fichier .vsz.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

Voici les parties du fichier .vsz.

|Élément|Description|
|----------|-----------------|
|VSWizard VSWizard|Le premier paramètre dans le fichier est le numéro de version du format de fichier de modèle. Ce numéro de version doit être de 6,0, 7,0, 7,1 ou 8,0. D’autres numéros ne peuvent pas être commencés et provoquer une erreur de format invalide.|
|Assistant|Ce champ contient l’OLE ProgID de l’assistant, ou alternativement une représentation de chaîne GUID du CLSID de l’assistant qui est cocréé par l’IDE.|
|Paramètre|Ces pièces sont facultatives. Vous pouvez ajouter autant que nécessaire.|

Les paramètres permettent au fichier .vsz de transmettre des paramètres personnalisés supplémentaires à l’assistant. Chaque valeur est passée comme un élément de chaîne dans un tableau de variantes à l’assistant. Pour plus d’informations, voir [Paramètres personnalisés](../../extensibility/internals/custom-parameters.md).

Pour ajouter un ID local par défaut `FALLBACK_LCID`à votre fichier .vsz, spécifiez le xxxx, où xxxx est l’ID local, par exemple, 1033 pour l’anglais. Lorsque `FALLBACK_LCID` le paramètre est défini, l’assistant utilise l’ID local de repli fourni si l’ID actuel n’est pas trouvé.

## <a name="see-also"></a>Voir aussi

- [Paramètres personnalisés](../../extensibility/internals/custom-parameters.md)
- [Assistants](../../extensibility/internals/wizards.md)
- [Fichiers de description de répertoire de modèles (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
