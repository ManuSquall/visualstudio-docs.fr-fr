---
title: Détails de configuration de contrôle des sources (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cf4a5c55e8093e5dcd6406cde1c60f642188495
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705293"
---
# <a name="source-control-configuration-details"></a>Détails de configuration du contrôle de code source
Afin de mettre en œuvre le contrôle source, vous devez configurer correctement votre système de projet ou votre éditeur pour faire ce qui suit :

- Demander la permission de passer à l’état changé

- Demander la permission d’enregistrer un fichier

- Demander la permission d’ajouter, de supprimer ou de renommer des fichiers dans le projet

## <a name="request-permission-to-transition-to-changed-state"></a>Demander l’autorisation de passer à l’état changé
 Un projet ou un éditeur doit demander la permission <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>de passer à l’état modifié (sale) en appelant . Chaque éditeur qui <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> met <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> en œuvre doit appeler et `True` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>recevoir l’approbation de modifier le document de l’environnement avant de revenir pour . Un projet est essentiellement rédacteur en chef d’un fichier de projet et, par conséquent, a la même responsabilité dans la mise en œuvre du suivi de l’état modifié pour le fichier de projet comme le fait un éditeur de texte pour ses fichiers. L’environnement gère l’état modifié de la solution, mais vous devez gérer l’état modifié de tout objet les références de solution, mais ne stocke pas, comme un fichier de projet ou ses éléments. En général, si votre projet ou éditeur est responsable de la gestion de la persistance d’un élément, il est responsable de la mise en œuvre du suivi de l’état modifié.

 En réponse `IVsQueryEditQuerySave2::QueryEditFiles` à l’appel, l’environnement peut faire ce qui suit :

- Rejeter l’appel au changement, auquel cas l’éditeur ou le projet doit rester dans l’état inchangé (propre).

- Indiquez que les données du document doivent être rechargées. Pour un projet, l’environnement rechargera les données du projet. Un éditeur doit recharger les <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> données à partir du disque jusqu’à sa mise en œuvre. Dans les deux cas, le contexte du projet ou de l’éditeur peut changer lorsque les données sont rechargées.

  Il s’agit d’une tâche `IVsQueryEditQuerySave2::QueryEditFiles` complexe et difficile de moderniser les appels appropriés sur une base de code existante. Par conséquent, ces appels doivent être intégrés lors de la création du projet ou de l’éditeur.

## <a name="request-permission-to-save-a-file"></a>Demander l’autorisation d’enregistrer un fichier
 Avant qu’un projet ou un <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> éditeur <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>enregistre un fichier, il doit appeler ou . Pour les fichiers de projet, ces appels sont automatiquement complétés par la solution, qui sait quand enregistrer un fichier de projet. Les éditeurs sont responsables de faire `IVsPersistDocData2` ces appels <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>à moins que la mise en œuvre de l’éditeur utilise la fonction d’aide . Si votre éditeur `IVsPersistDocData2` implémente de `IVsQueryEditQuerySave2::QuerySaveFile` cette `IVsQueryEditQuerySave2::QuerySaveFiles` façon, alors l’appel ou est fait pour vous.

> [!NOTE]
> Faites toujours ces appels de façon préventive, c’est-à-dire à un moment où votre éditeur est en mesure de recevoir une annulation.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Demander l’autorisation d’ajouter, de supprimer ou de renommer les fichiers dans le projet
 Avant qu’un projet puisse ajouter, renommer ou supprimer un fichier `IVsTrackProjectDocuments2::OnQuery*` ou un répertoire, il doit appeler la méthode appropriée pour demander la permission de l’environnement. Si l’autorisation est accordée, le projet doit `IVsTrackProjectDocuments2::OnAfter*` effectuer l’opération et ensuite appeler la méthode appropriée pour aviser l’environnement que l’opération est terminée. Le projet doit appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> les méthodes de l’interface pour tous les fichiers (par exemple, fichiers spéciaux) et pas seulement les fichiers parent. Les appels de fichiers sont obligatoires, mais les appels d’annuaire sont facultatifs. Si votre projet a des informations d’annuaire, alors il devrait appeler les méthodes appropriées, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> mais s’il n’a pas cette information, alors l’environnement inférera des informations d’annuaire.

 Le projet ne doit `IVsTrackProjectDocuments2` pas appeler les méthodes de projet ouvert ou fermé. Les auditeurs qui veulent cette <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> information en démarrage peuvent attendre l’événement et itérer à travers la solution pour trouver les informations dont ils ont besoin. À l’arrêt, cette information n’est pas nécessaire. `IVsTrackProjectDocuments2`est fourni <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>à partir de la .

 Pour chaque ajout, renommer et supprimer l’action, il existe une `OnQuery*` méthode et une `OnAfter*` méthode. Appelez `OnQuery*` la méthode pour demander la permission d’ajouter, de renommer ou de supprimer le fichier ou l’annuaire. Appelez `OnAfter*` la méthode après que le fichier ou l’annuaire a été ajouté, renommé, ou supprimé et l’état du projet reflète le nouvel état.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Prise en charge du contrôle de code source](../../extensibility/internals/supporting-source-control.md)
