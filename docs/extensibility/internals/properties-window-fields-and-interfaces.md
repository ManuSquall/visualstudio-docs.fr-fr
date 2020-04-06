---
title: Propriétés Window Fields and Interfaces (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9529708c781e7fdb04c3b4c5ee143b7605857e84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706161"
---
# <a name="properties-window-fields-and-interfaces"></a>Champs et interfaces de la fenêtre Propriétés
Le modèle de sélection pour déterminer quelles informations sont affichées dans la fenêtre **Propriétés** est basé sur la fenêtre qui a mis l’accent dans l’IDE. Chaque fenêtre et objet dans la fenêtre sélectionnée peuvent avoir son objet de contexte de sélection poussé au contexte global de sélection. L’environnement met à jour le contexte de sélection global avec des valeurs à partir d’un cadre de fenêtre lorsque cette fenêtre a la mise au point. Lorsque l’accent change, le contexte de sélection aussi.

## <a name="tracking-selection-in-the-ide"></a>Sélection de suivi dans l’IDE
 Le cadre de fenêtre ou le site, appartenant <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>à l’IDE, a un service appelé . Les étapes suivantes montrent comment un changement dans une sélection, causé par l’utilisateur soit changer de mise au point vers une autre fenêtre ouverte ou de sélectionner un élément de projet différent dans **Solution Explorer**, est implémenté pour changer le contenu affiché dans la fenêtre **Propriétés.**

1. L’objet créé par votre VSPackage qui est <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> situé <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>dans les appels de fenêtre sélectionnés pour avoir invoque .

2. Le conteneur de sélection, fourni par <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> la fenêtre sélectionnée, crée son propre objet. Lorsque la sélection change, le <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> VSPackage appelle à aviser les auditeurs dans l’environnement, y compris la fenêtre **Propriétés,** de la modification. Il donne également accès à la hiérarchie et aux informations sur les éléments liés à la nouvelle sélection.

3. L’appeler <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> et le passer `VSHPROPID_BrowseObject` les éléments <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> de hiérarchie sélectionnés dans le paramètre peuple l’objet.

4. Un objet dérivé de [l’interface IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) est retourné pour [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) pour l’article demandé, et l’environnement <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> l’enveloppe dans un (voir l’étape suivante). Si l’appel échoue, l’environnement `IVsHierarchy::GetProperty`fait un deuxième appel à , en passant le conteneur de sélection [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) que l’élément de hiérarchie ou les éléments fournissent.

    Votre projet VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> ne crée pas parce que la fenêtre fournie par l’environnement <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> VSPackage qui l’implémente (par exemple, Solution **Explorer**) construit en son nom.

5. L’environnement invoque <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> les méthodes d’obtenir les objets en fonction de l’interface `IDispatch` pour remplir la fenêtre **Propriétés.**

   Lorsqu’une valeur dans la fenêtre **Propriétés** `IVsTrackSelectionEx::OnElementValueChangeEx` est `IVsTrackSelectionEx::OnSelectionChangeEx` modifiée, VSPackages implémente et signale la modification de la valeur de l’élément. L’environnement invoque alors ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> pour garder les informations affichées dans la fenêtre **propriété** synchronisée avec les valeurs de la propriété. Pour plus d’informations, voir [Mise à jour des valeurs de propriété dans la fenêtre des propriétés](#updating-property-values-in-the-properties-window).

   En plus de sélectionner un élément de projet différent dans **Solution Explorer** pour afficher les propriétés liées à cet élément, vous pouvez également choisir un objet différent à partir d’un formulaire ou d’une fenêtre de document à l’aide de la liste de dépôt disponible sur la fenêtre **Propriétés.** Pour plus d’informations, voir [Properties Window Object List](../../extensibility/internals/properties-window-object-list.md).

   Vous pouvez modifier la façon dont les informations sont affichées dans la grille de fenêtre **Propriétés** de l’alphabetique à la catégorie, et, si disponible, vous pouvez également ouvrir une page de propriété pour un objet sélectionné en cliquant sur les boutons appropriés sur la fenêtre **propriété.** Pour plus d’informations, voir [Boutons de fenêtre des propriétés](../../extensibility/internals/properties-window-buttons.md) et pages de [propriété](../../extensibility/internals/property-pages.md).

   Enfin, le bas de la fenêtre **Propriétés** contient également une description du champ sélectionné dans la grille de fenêtre **Propriétés.** Pour plus d’informations, voir [Getting Field Descriptions from the Properties Window](#getting-field-descriptions-from-the-properties-window).

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a>Mise à jour des valeurs foncières dans la fenêtre des propriétés
Il existe deux façons de garantir la synchronisation de la fenêtre **Propriétés** avec les valeurs de propriété mises à jour. La première consiste à appeler l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>, qui donne accès aux fonctionnalités de base de fenêtrage, y compris l’utilisation et la création de fenêtres Outil et de document fournies par l’environnement. Les étapes qui suivent décrivent ce processus de synchronisation.

### <a name="updating-property-values-using-ivsuishell"></a>Mise à jour des valeurs de propriété à l’aide de l’interface IVsUIShell

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Pour mettre à jour les valeurs de propriété à l’aide de l’interface IVsUIShell

1. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (via le service <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>) quand un VSPackage, projet ou éditeur doit créer ou énumérer une fenêtre Outil ou de document.

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> Implémentez pour maintenir la fenêtre **Propriétés** en phase avec les modifications de propriété <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> pour <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> un projet (ou tout autre objet sélectionné étant parcouru par la fenêtre **propriété)** sans mise en œuvre et les événements de mise à pied.

3. Implémentez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> pour activer ou désactiver, respectivement, la notification par le client des événements de la hiérarchie (cette hiérarchie n’a alors pas besoin d’implémenter <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>).

### <a name="updating-property-values-using-iconnection"></a>Mise à jour des valeurs de propriété à l’aide de l’interface IConnection
 La deuxième façon de garantir la synchronisation de la fenêtre **Propriétés** avec les valeurs de propriété mises à jour consiste à implémenter `IConnection` sur l’objet connectable pour indiquer l’existence des interfaces sortantes. Si vous souhaitez localiser le nom de propriété, dérivez votre objet de l’élément <xref:System.ComponentModel.ICustomTypeDescriptor>. L’implémentation de l’élément <xref:System.ComponentModel.ICustomTypeDescriptor> peut modifier les descripteurs de propriété renvoyés et modifier le nom d’une propriété. Pour localiser la description, créez un attribut dérivé de l’élément <xref:System.ComponentModel.DescriptionAttribute> et remplacez la propriété Description.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Considérations relatives à l’implémentation de l’interface IConnection

1. `IConnection` fournit l’accès à un sous-objet énumérateur avec l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. Elle fournit aussi l’accès à tous les sous-objets point de connexion, chacun d’eux implémentant l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>.

2. Chaque objet parcouru doit implémenter un événement <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>. La fenêtre **Propriétés** affiche des conseils sur l’événement défini via `IConnection`.

3. Un point de connexion détermine le nombre de connexions (une seule ou plusieurs) qu’il autorise dans son implémentation d’<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Un point de connexion autorisant une seule interface peut renvoyer <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> de la méthode <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>.

4. Un client peut appeler l’interface `IConnection` pour obtenir l’accès à un sous-objet énumérateur avec l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. L’interface <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> peut ensuite être appelée pour énumérer les points de connexion pour chaque ID d’interface sortante (IID).

5. L’interface `IConnection` peut également être appelée pour obtenir l’accès aux sous-objets point de connexion avec l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> pour chaque IID sortant. Grâce <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> à l’interface, un client démarre ou met fin à une boucle de conseil avec l’objet connectable et la synchronisation du client. Le client peut <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> également appeler l’interface pour obtenir <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> un objet d’enumérateur avec l’interface pour énumérer les connexions qu’il connaît.

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a>Obtenir des descriptions de champ à partir de la fenêtre des propriétés
En bas de la fenêtre **Propriétés** , une zone de description affiche des informations relatives au champ de propriété sélectionné. Cette fonctionnalité est activée par défaut. Si vous voulez masquer le champ de description, cliquez avec le bouton droit sur la fenêtre **Propriétés** et cliquez sur **Description**. Cette action supprime également la coche à côté du titre **Description** dans la fenêtre de menu. Vous pouvez afficher le champ à nouveau en suivant la même procédure pour réactiver **Description** .

 Les informations du champ de description proviennent de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Chaque méthode, interface, coclasse, etc. peut avoir un attribut `helpstring` non localisé dans la bibliothèque de types. La fenêtre **Properties** récupère <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>la chaîne de .

### <a name="to-specify-localized-help-strings"></a>Pour spécifier des chaînes d’aide localisées

1. Ajoutez l’attribut `helpstringdll` à l’instruction library dans la bibliothèque de types (`typelib`).

   > [!NOTE]
   > Cette étape est facultative si la bibliothèque de types se trouve dans un fichier de bibliothèque d’objets (.olb).

2. Spécifiez des attributs `helpstringcontext` pour les chaînes. Vous pouvez également spécifier des attributs `helpstring` .

    Ces attributs sont distincts des attributs `helpfile` et `helpcontext` qui sont contenus dans les vraies rubriques d’aide du fichier .chm.

   Pour récupérer les informations de description à afficher pour <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> le nom de propriété en surbrillance, la fenêtre **Propriétés** appelle pour la propriété qui est sélectionnée, spécifiant l’attribut souhaité `lcid` pour la chaîne de sortie. En interne, <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> recherche le fichier .dll spécifié dans l’attribut `helpstringdll` et appelle `DLLGetDocumentation` sur ce fichier .dll avec le contexte spécifié et l’attribut `lcid`.

   La signature et l’implémentation de `DLLGetDocumentation` sont les suivantes :

```cpp
STDAPI DLLGetDocumentation
(
   ITypeLib * /* ptlib */,
   ITypeInfo * /* ptinfo */,
   LCID /* lcid */,
   DWORD dwCtx,
   BSTR * pbstrHelpString
);
```

 La fonction `DLLGetDocumentation` doit être une exportation définie dans le fichier .def pour la DLL.

 En interne, un fichier .olb est créé, qui est effectivement une DLL. Cette DLL contient une ressource, le fichier de bibliothèque de types (.tlb) et une fonction exportée, `DLLGetDocumentation`.

 Dans le cas des fichiers .olb, l’attribut `helpstringdll` est facultatif, car il s’agit du même fichier qui contient le fichier .tlb lui-même.

 Par conséquent, pour que des chaînes s’affichent dans le volet **Descriptions** , vous devez au moins spécifier l’attribut `helpstring` dans la bibliothèque de types. Si vous voulez que ces chaînes soient localisées, vous devez spécifier l’attribut `helpstringdll` (facultatif) et l’attribut `helpstringcontext` (obligatoire), et implémenter `DLLGetDocumentation`.

 Aucune autre interface ne doit être implémentée lors de la localisation d’informations par le biais de l’attribut `helpstringcontext` d’idl et `DLLGetDocumentation`.

  Pour obtenir le nom et la description localisés d’une propriété, vous pouvez aussi implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Pour plus d’informations sur l’implémentation de cette méthode, consultez [Properties Window Fields and Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md).

## <a name="see-also"></a>Voir aussi

- [Extension des propriétés](../../extensibility/internals/extending-properties.md)
