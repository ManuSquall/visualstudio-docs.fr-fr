---
title: "Résoudre les problèmes liés au chargement des modèles de projet et d’élément Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d9242d053044fa66e6eb3d506382cf7cfb5d0295
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-troubleshoot-templates"></a>Guide pratique pour résoudre les problèmes de modèles

Si le chargement d’un modèle dans l’environnement de développement échoue, il existe plusieurs façons de procéder pour localiser le problème.

## <a name="validate-the-vstemplate-file"></a>Valider le fichier .vstemplate

Si le fichier .vstemplate d’un modèle n’adhère pas au schéma de modèle Visual Studio, il se peut que le modèle n’apparaisse pas dans la boîte de dialogue **Nouveau projet**.

### <a name="to-validate-the-vstemplate-file"></a>Pour valider le fichier .vstemplate

1. Localisez le fichier .zip qui contient le modèle.

1. Extrayez le fichier zip.

1. Dans le menu **Fichier** de Visual Studio, choisissez **Ouvrir** > **Fichier**.

1. Sélectionnez le fichier .vstemplate du modèle, puis choisissez **Ouvrir**.

1. Vérifiez que le code XML du fichier .vstemplate adhère au schéma du modèle. Pour plus d’informations sur le schéma .vstemplate, consultez [Informations de référence sur les schémas de modèles](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Pour obtenir une prise en charge d’IntelliSense quand vous créez le fichier .vstemplate, ajoutez un attribut `xmlns` à l’élément `VSTemplate` et attribuez-lui la valeur http://schemas.microsoft.com/developer/vstemplate/2005.

1. Enregistrez et fermez le fichier .vstemplate. 

1. Sélectionnez les fichiers inclus dans votre modèle, cliquez avec le bouton droit, puis choisissez **Envoyer vers** > **Dossier compressé**. Les fichiers que vous avez sélectionnés sont compressés dans un fichier .zip.

1. Placez le nouveau fichier .zip dans le même répertoire que l’ancien fichier .zip.

1. Supprimez les fichiers de modèles extraits et l'ancien fichier .zip du modèle.

## <a name="enable-diagnostic-logging"></a>Activer la journalisation des diagnostics

Vous pouvez activer la journalisation des diagnostics pour la découverte de modèles en suivant les étapes indiquées dans [Résolution des problèmes de découverte de modèles (extensibilité)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>Voir aussi

[Résolution des problèmes de découverte de modèles (extensibilité)](../extensibility/troubleshooting-template-discovery.md)  
[Personnalisation des modèles](../ide/customizing-project-and-item-templates.md)  
[Création de modèles de projets et d’éléments](../ide/creating-project-and-item-templates.md)  
[Informations de référence sur les schémas de modèles](../extensibility/visual-studio-template-schema-reference.md)