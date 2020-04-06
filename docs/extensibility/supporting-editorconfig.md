---
title: Étendre le service linguistique pour soutenir EditorConfig
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddfe0e30904d000b4fd70c85371d29a2ee486932
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699585"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Soutenir EditorConfig pour votre service linguistique

[EditorConfig](https://editorconfig.org/) fichiers vous permettent de décrire les options courantes d’éditeur de texte, telles que la taille de l’indent, sur une base par projet. Pour en savoir plus sur le support de Visual Studio pour les fichiers EditorConfig, consultez [les paramètres de l’éditeur portable Create à l’aide de EditorConfig](../ide/create-portable-custom-editor-options.md).

Dans la plupart des cas, quand vous implémentez un service de langage Visual Studio, aucun travail supplémentaire n’est nécessaire pour la prise en charge des propriétés universelles EditorConfig. L’éditeur principal découvre et lit automatiquement le fichier .editorconfig quand les utilisateurs ouvrent des fichiers, et définit les options d’affichage et de mémoire tampon de texte appropriées. Toutefois, pour les modifications telles que les onglets et les espaces, certains services linguistiques choisissent d’utiliser une option de vue contextuelle appropriée plutôt que d’utiliser des paramètres globaux. Dans ce cas, le service de langage doit être mis à jour pour prendre en charge les fichiers EditorConfig.

Voici les modifications nécessaires pour mettre à jour un service linguistique pour prendre en charge les fichiers EditorConfig, en remplaçant une option mondiale _spécifique à la langue_ par une option _contextuelle_ :

## <a name="indent-style"></a>Style de mise en retrait

Options spécifiques à la langue | Options contextuelles
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Taille du retrait

Options spécifiques à la langue | Options contextuelles
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Taille des tabulation

Options spécifiques à la langue | Options contextuelles
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Voir aussi

- [Créez des paramètres d’éditeur portables à l’aide de EditorConfig](../ide/create-portable-custom-editor-options.md)
- [Élargir les services d’éditeur et de langue](../extensibility/extending-the-editor-and-language-services.md)
