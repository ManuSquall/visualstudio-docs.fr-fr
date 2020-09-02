---
title: Étendre le service de langage pour prendre en charge EditorConfig
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699585"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Prise en charge de EditorConfig pour votre service de langage

Les fichiers [EditorConfig](https://editorconfig.org/) vous permettent de décrire des options d’éditeur de texte courantes, telles que la taille du retrait, pour chaque projet. Pour en savoir plus sur la prise en charge de Visual Studio pour les fichiers EditorConfig, consultez [créer des paramètres d’éditeur portable à l’aide de EditorConfig](../ide/create-portable-custom-editor-options.md).

Dans la plupart des cas, quand vous implémentez un service de langage Visual Studio, aucun travail supplémentaire n’est nécessaire pour la prise en charge des propriétés universelles EditorConfig. L’éditeur principal découvre et lit automatiquement le fichier .editorconfig quand les utilisateurs ouvrent des fichiers, et définit les options d’affichage et de mémoire tampon de texte appropriées. Toutefois, pour les modifications telles que les tabulations et les espaces, certains services de langage choisissent d’utiliser une option d’affichage de texte contextuelle appropriée plutôt que d’utiliser des paramètres globaux. Dans ce cas, le service de langage doit être mis à jour pour prendre en charge les fichiers EditorConfig.

Voici les modifications nécessaires pour mettre à jour un service de langage afin de prendre en charge les fichiers EditorConfig, en remplaçant une option globale spécifique à une _langue_ par une option _contextuelle_ :

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

- [Créer des paramètres d’éditeur portable à l’aide de EditorConfig](../ide/create-portable-custom-editor-options.md)
- [Extension de l’éditeur et des services de langage](../extensibility/extending-the-editor-and-language-services.md)
