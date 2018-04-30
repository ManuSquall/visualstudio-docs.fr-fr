---
title: Résoudre les problèmes liés au chargement des modèles de projet et d’élément Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: f7e952f8eb445787a2a574ae3431ba6ad8728248
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-troubleshoot-templates"></a>Guide pratique pour résoudre les problèmes de modèles

Si le chargement d’un modèle dans l’environnement de développement échoue, il existe plusieurs façons de procéder pour localiser le problème.

## <a name="validate-the-vstemplate-file"></a>Valider le fichier .vstemplate

Si le fichier *.vstemplate* d’un modèle n’adhère pas au schéma de modèle Visual Studio, il se peut que le modèle n’apparaisse pas dans la boîte de dialogue **Nouveau projet**.

### <a name="to-validate-the-vstemplate-file"></a>Pour valider le fichier .vstemplate

1. Localisez le fichier *.zip* qui contient le modèle.

1. Extrayez le fichier *.zip*.

1. Dans le menu **Fichier** de Visual Studio, choisissez **Ouvrir** > **Fichier**.

1. Sélectionnez le fichier *.vstemplate* du modèle, puis choisissez **Ouvrir**.

1. Vérifiez que le code XML du fichier *.vstemplate* adhère au schéma de modèle. Pour plus d’informations sur le schéma *.vstemplate*, consultez [Informations de référence sur les schémas de modèles](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Pour obtenir une prise en charge d’IntelliSense quand vous créez le fichier *.vstemplate*, ajoutez un attribut `xmlns` à l’élément `VSTemplate`, puis affectez-lui la valeur http://schemas.microsoft.com/developer/vstemplate/2005.

1. Enregistrez et fermez le fichier *.vstemplate*.

1. Sélectionnez les fichiers inclus dans votre modèle, cliquez avec le bouton droit, puis choisissez **Envoyer vers** > **Dossier compressé**. Les fichiers que vous avez sélectionnés sont compressés dans un fichier *.zip*.

1. Placez le nouveau fichier *.zip* dans le même répertoire que l’ancien fichier *.zip*.

1. Supprimez les fichiers de modèles extraits et l’ancien fichier *.zip* de modèle.

## <a name="enable-diagnostic-logging"></a>Activer la journalisation des diagnostics

Vous pouvez activer la journalisation des diagnostics pour la découverte de modèles en suivant les étapes indiquées dans [Résoudre les problèmes de découverte de modèles (extensibilité)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>Voir aussi

[Résoudre les problèmes de découverte de modèles (extensibilité)](../extensibility/troubleshooting-template-discovery.md)  
[Personnaliser les modèles](../ide/customizing-project-and-item-templates.md)  
[Créer des modèles de projet et d’élément](../ide/creating-project-and-item-templates.md)  
[Informations de référence sur les schémas de modèles](../extensibility/visual-studio-template-schema-reference.md)