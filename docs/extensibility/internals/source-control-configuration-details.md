---
title: Détails de Configuration de contrôle de la source | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85ba74ba9d9beabaefd22607df0fac6ebaaf2235
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825931"
---
# <a name="source-control-configuration-details"></a>Détails de configuration du contrôle de code source
Pour implémenter le contrôle de code source, vous devez configurer correctement votre système de projet ou d’un éditeur pour effectuer les opérations suivantes :

-   Demander l’autorisation à passer à l’état modifié

-   Demander l’autorisation d’enregistrer un fichier

-   Demander l’autorisation d’ajouter, supprimer ou renommer des fichiers dans le projet

## <a name="request-permission-to-transition-to-changed-state"></a>Demander l’autorisation à passer à l’état modifié
 Un projet ou un éditeur doit demander une autorisation pour la transition vers l’état modifié (« Dirty ») en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>. Chaque éditeur implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> doit appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> et recevoir une approbation pour modifier le document à partir de l’environnement avant de retourner `True` pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>. Un projet est essentiellement un éditeur pour un fichier de projet et par conséquent, a la responsabilité de même pour l’implémentation de suivi de l’état modifié pour le fichier projet comme un éditeur de texte pour ses fichiers. L’environnement gère l’état modifié de la solution, mais vous devez gérer l’état modifié de n’importe quel objet fait référence à la solution mais ne stocke pas, comme un fichier de projet ou de ses éléments. En règle générale, si votre éditeur ou un projet est chargé de gérer la persistance pour un élément, il est chargé d’implémenter le suivi de l’état modifié.

 En réponse à la `IVsQueryEditQuerySave2::QueryEditFiles` appeler, l’environnement pouvez procédez comme suit :

- Rejeter l’appel à modifier, auquel cas l’éditeur ou un projet doit rester dans un état unchanged (nettoyage).

- Indiquer que les données du document doivent être rechargées. Pour un projet, l’environnement recharge les données pour le projet. Un éditeur doit recharger les données à partir du disque via son <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> implémentation. Dans les deux cas, le contexte dans le projet ou un éditeur peut changer lors du rechargement de données.

  C’est une tâche complexe et difficile à adapter a posteriori approprié `IVsQueryEditQuerySave2::QueryEditFiles` appels sur une base de code existante. Par conséquent, ces appels doivent être intégrées lors de la création du projet ou de l’éditeur.

## <a name="request-permission-to-save-a-file"></a>Demander l’autorisation d’enregistrer un fichier
 Avant qu’un projet ou un éditeur enregistre un fichier, il doit appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>. Pour les fichiers de projet, ces appels sont automatiquement effectuées par la solution, qui sait à quel moment d’enregistrer un fichier de projet. Les éditeurs sont responsables de l’exécution de ces appels, sauf si l’implémentation de l’éditeur de `IVsPersistDocData2` utilise la fonction d’assistance <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>. Si votre éditeur implémente `IVsPersistDocData2` de cette façon, puis l’appel à `IVsQueryEditQuerySave2::QuerySaveFile` ou `IVsQueryEditQuerySave2::QuerySaveFiles` est faite pour vous.

> [!NOTE]
>  Toujours effectuer ces appels à titre préventif, autrement dit, à la fois lorsque votre éditeur est en mesure de recevoir une annulation.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Demander l’autorisation d’ajouter, supprimer ou renommer des fichiers dans le projet
 Avant d’un projet peut ajouter, renommer ou supprimer un fichier ou répertoire, il doit appeler approprié `IVsTrackProjectDocuments2::OnQuery*` méthode pour demander l’autorisation à partir de l’environnement. Si l’autorisation est accordée, le projet doit effectuer l’opération, puis appelez approprié `IVsTrackProjectDocuments2::OnAfter*` méthode pour notifier l’environnement que l’opération est terminée. Le projet doit appeler les méthodes de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interface pour tous les fichiers (par exemple, des fichiers spéciaux) et pas seulement les fichiers de parent. Appels de fichier sont obligatoires, mais les appels d’annuaire sont facultatifs. Si votre projet comporte des informations d’annuaire, il doit appeler approprié <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> méthodes, mais si elle n’a pas de ces informations, l’environnement sera déduite des informations d’annuaire.

 Le projet ne doit pas appeler les méthodes de `IVsTrackProjectDocuments2` au projet ouvrir ou fermer. Les écouteurs qui souhaitent que ces informations au démarrage peuvent attendre le <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> événements et effectuer une itération dans la solution pour trouver les informations dont ils ont besoin. Lors de l’arrêt, ces informations ne sont pas nécessaires. `IVsTrackProjectDocuments2` est fourni à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.

 Pour chaque ajouter, renommer et action de suppression, il existe un `OnQuery*` (méthode) et un `OnAfter*` (méthode). Appelez le `OnQuery*` méthode pour demander l’autorisation d’ajouter, renommer ou supprimer le fichier ou répertoire. Appelez le `OnAfter*` méthode une fois que le fichier ou répertoire a été ajouté, renommé ou supprimé et l’état du projet reflète le nouvel état.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Prise en charge du contrôle de code source](../../extensibility/internals/supporting-source-control.md)