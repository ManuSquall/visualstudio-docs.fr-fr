---
title: "Extension d’un service de langage pour prendre en charge EditorConfig dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 111e53ad9beec3a5f5ef013b996a541ea0fa1e72
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2017
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Prise en charge de EditorConfig pour votre service de langage

[EditorConfig](http://editorconfig.org/) fichiers permettent de vous permettent de décrire les options d’éditeur de texte courantes, telles que la taille mise en retrait, sur une base par projet. Pour en savoir plus sur la prise en charge de Visual Studio pour les fichiers EditorConfig, consultez [créer les paramètres de l’éditeur portable à l’aide de EditorConfig](../ide/create-portable-custom-editor-options.md).

Dans la plupart des cas, quand vous implémentez un service de langage Visual Studio, aucun travail supplémentaire n’est nécessaire pour la prise en charge des propriétés universelles EditorConfig. L’éditeur principal découvre et lit automatiquement le fichier .editorconfig quand les utilisateurs ouvrent des fichiers, et définit les options d’affichage et de mémoire tampon de texte appropriées. Toutefois, pour les modifications telles que les tabulations et des espaces, certains services de langage tourner une option d’affichage de texte contextuelles approprié au lieu d’utiliser les paramètres globaux. Dans ce cas, le service de langage doit être mis à jour pour prendre en charge les fichiers EditorConfig.

Voici les modifications qui sont nécessaires pour mettre à jour un service de langage pour prendre en charge les fichiers EditorConfig, en remplaçant global _spécifiques au langage_ option avec un _contextuelles_ option :

## <a name="indent-style"></a>Style de mise en retrait

Options spécifiques aux langues | Options contextuelles
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|! textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>! textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Taille du retrait

Options spécifiques aux langues | Options contextuelles
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Taille des tabulations

Options spécifiques aux langues | Options contextuelles
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Voir aussi

[Créer des paramètres de l’éditeur portable à l’aide de EditorConfig](../ide/create-portable-custom-editor-options.md)  
[Extension des services de l’éditeur et la langue](../extensibility/extending-the-editor-and-language-services.md)