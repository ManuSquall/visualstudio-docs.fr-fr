---
title: Détails de la configuration du contrôle de code source | Microsoft Docs
description: Découvrez comment implémenter le contrôle de code source pour un type de projet dans Visual Studio, ce qui implique la configuration de votre système ou éditeur de projet pour demander des autorisations.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b9a3a2f33fcbb94d1e863daf69b8561f7bad4f2a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846502"
---
# <a name="source-control-configuration-details"></a>Détails de configuration du contrôle de code source
Pour implémenter le contrôle de code source, vous devez configurer correctement votre système ou éditeur de projet pour effectuer les opérations suivantes :

- Demander l’autorisation de passer à l’état modifié

- Demander l’autorisation d’enregistrer un fichier

- Demander l’autorisation d’ajouter, de supprimer ou de renommer des fichiers dans le projet

## <a name="request-permission-to-transition-to-changed-state"></a>Demander l’autorisation de passer à l’état modifié
 Un projet ou un éditeur doit demander l’autorisation de passer à l’état modifié (modifié) en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> . Chaque éditeur qui implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> doit appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> et recevoir l’approbation pour modifier le document de l’environnement avant `True` de retourner pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> . Un projet est essentiellement un éditeur pour un fichier projet et, par conséquent, a la même responsabilité pour implémenter le suivi de l’état modifié pour le fichier projet qu’un éditeur de texte pour ses fichiers. L’environnement gère l’état modifié de la solution, mais vous devez gérer l’état modifié de tout objet que la solution référence, mais ne stocke pas, comme un fichier projet ou ses éléments. En général, si votre projet ou éditeur est responsable de la gestion de la persistance pour un élément, il est chargé d’implémenter le suivi de l’état modifié.

 En réponse à l' `IVsQueryEditQuerySave2::QueryEditFiles` appel, l’environnement peut effectuer les opérations suivantes :

- Rejeter l’appel à change, auquel cas l’éditeur ou le projet doit rester dans l’État inchangé (Clean).

- Indique que les données du document doivent être rechargées. Pour un projet, l’environnement recharge les données pour le projet. Un éditeur doit recharger les données à partir du disque par le biais de son <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implémentation. Dans les deux cas, le contexte du projet ou de l’éditeur peut changer lors du rechargement des données.

  Il s’agit d’une tâche complexe et difficile pour répartir les `IVsQueryEditQuerySave2::QueryEditFiles` appels appropriés sur une base de code existante. Par conséquent, ces appels doivent être intégrés lors de la création du projet ou de l’éditeur.

## <a name="request-permission-to-save-a-file"></a>Demander l’autorisation d’enregistrer un fichier
 Avant qu’un projet ou un éditeur n’enregistre un fichier, il doit appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> . Pour les fichiers projet, ces appels sont automatiquement effectués par la solution, qui sait quand enregistrer un fichier projet. Les éditeurs sont chargés d’effectuer ces appels, sauf si l’implémentation de l’éditeur de `IVsPersistDocData2` utilise la fonction d’assistance <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> . Si votre éditeur implémente `IVsPersistDocData2` de cette manière, l’appel à `IVsQueryEditQuerySave2::QuerySaveFile` ou `IVsQueryEditQuerySave2::QuerySaveFiles` est effectué pour vous.

> [!NOTE]
> Effectuez toujours ces appels de manière préventive, c’est-à-dire lorsque votre éditeur est en mesure de recevoir une annulation.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Demander l’autorisation d’ajouter, de supprimer ou de renommer des fichiers dans le projet
 Avant qu’un projet puisse ajouter, renommer ou supprimer un fichier ou un répertoire, il doit appeler la `IVsTrackProjectDocuments2::OnQuery*` méthode appropriée pour demander une autorisation à partir de l’environnement. Si l’autorisation est accordée, le projet doit terminer l’opération, puis appeler la `IVsTrackProjectDocuments2::OnAfter*` méthode appropriée pour notifier l’environnement que l’opération est terminée. Le projet doit appeler les méthodes de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interface pour tous les fichiers (par exemple, des fichiers spéciaux) et pas seulement les fichiers parents. Les appels de fichier sont obligatoires, mais les appels de répertoire sont facultatifs. Si votre projet contient des informations d’annuaire, il doit appeler les <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> méthodes appropriées, mais s’il ne dispose pas de ces informations, l’environnement déduirea les informations d’annuaire.

 Le projet ne doit pas appeler les méthodes de `IVsTrackProjectDocuments2` at Project Open ou Close. Les écouteurs qui souhaitent ces informations au démarrage peuvent attendre l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> événement et itérer au sein de la solution pour trouver les informations dont elles ont besoin. Lors de l’arrêt, ces informations ne sont pas nécessaires. `IVsTrackProjectDocuments2` est fourni à partir de <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> .

 Pour chaque action d’ajout, de renommage et de suppression, il existe une `OnQuery*` méthode et une `OnAfter*` méthode. Appelez la `OnQuery*` méthode pour demander l’autorisation d’ajouter, de renommer ou de supprimer le fichier ou le répertoire. Appelez la `OnAfter*` méthode une fois que le fichier ou le répertoire a été ajouté, renommé ou supprimé et que l’état du projet reflète le nouvel État.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Prise en charge du contrôle de code source](../../extensibility/internals/supporting-source-control.md)
