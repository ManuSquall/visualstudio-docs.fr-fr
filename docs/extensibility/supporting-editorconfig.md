---
title: Extension d’un service de langage pour prendre en charge d’EditorConfig dans Visual Studio | Microsoft Docs
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3c29c22ae4539d874ffc08c9ce5adf94ab33d404
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696972"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Prise en charge d’EditorConfig pour votre service de langage

[EditorConfig](http://editorconfig.org/) fichiers permettent de décrire des options d’éditeur de texte courants, tels que la taille de la mise en retrait, sur une base par projet. Pour en savoir plus sur le support de Visual Studio pour les fichiers EditorConfig, consultez [créer des paramètres de l’éditeur de portables à l’aide d’EditorConfig](../ide/create-portable-custom-editor-options.md).

Dans la plupart des cas, quand vous implémentez un service de langage Visual Studio, aucun travail supplémentaire n’est nécessaire pour la prise en charge des propriétés universelles EditorConfig. L’éditeur principal découvre et lit automatiquement le fichier .editorconfig quand les utilisateurs ouvrent des fichiers, et définit les options d’affichage et de mémoire tampon de texte appropriées. Toutefois, pour les modifications telles que des tabulations et des espaces, certains services de langage choisissent pour utiliser une option d’affichage de texte contextuel appropriée, plutôt que d’utiliser les paramètres globaux. Dans ce cas, le service de langage doit être mis à jour pour prendre en charge les fichiers EditorConfig.

Voici les modifications qui sont nécessaires pour mettre à jour un service de langage pour prendre en charge les fichiers EditorConfig, en remplaçant un global _spécifiques au langage_ option avec un _contextuelles_ option :

## <a name="indent-style"></a>Style de mise en retrait

Options spécifiques au langage | Options contextuelles
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Taille du retrait

Options spécifiques au langage | Options contextuelles
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Taille des tabulations

Options spécifiques au langage | Options contextuelles
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Voir aussi

- [Créer des paramètres de l’éditeur de portables à l’aide d’EditorConfig](../ide/create-portable-custom-editor-options.md)
- [Extension des services de l’éditeur et la langue](../extensibility/extending-the-editor-and-language-services.md)