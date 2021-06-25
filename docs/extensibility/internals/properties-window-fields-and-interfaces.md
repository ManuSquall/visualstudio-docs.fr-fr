---
title: Champs et interfaces de la fenêtre Propriétés | Microsoft Docs
description: En savoir plus sur la sélection qui détermine quelles informations sont affichées dans le Fenêtre Propriétés en fonction de la fenêtre qui a le focus dans l’IDE de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7a74e82480d1a4c71179c0e0b0671bac4ae97191
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899626"
---
# <a name="properties-window-fields-and-interfaces"></a>Champs et interfaces de la fenêtre Propriétés
Le modèle de sélection permettant de déterminer les informations qui s’affichent dans la fenêtre **Propriétés** est basé sur la fenêtre qui a le focus dans l’IDE. Chaque fenêtre et objet dans la fenêtre sélectionnée peut faire l’objet d’un push de l’objet de contexte de sélection dans le contexte de sélection global. L’environnement met à jour le contexte de sélection global avec les valeurs d’un frame de fenêtre lorsque cette fenêtre a le focus. Lorsque le focus change, le contexte de sélection est donc sélectionné.

## <a name="tracking-selection-in-the-ide"></a>Suivi de la sélection dans l’IDE
 Le cadre de la fenêtre ou le site, appartenant à l’IDE, a un service appelé <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . Les étapes suivantes montrent comment une modification d’une sélection, provoquée par l’utilisateur à modifier le focus vers une autre fenêtre ouverte ou à sélectionner un autre élément de projet dans **Explorateur de solutions**, est implémentée pour modifier le contenu affiché dans la fenêtre **Propriétés** .

1. L’objet créé par le VSPackage qui est sur site dans la fenêtre sélectionnée appelle <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> pour qu’il appelle <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Invoke <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .

2. Le conteneur de sélection, fourni par la fenêtre sélectionnée, crée son propre <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objet. Lorsque la sélection change, le VSPackage appelle <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> pour notifier tous les écouteurs de l’environnement, y compris la fenêtre **Propriétés** , de la modification. Il permet également d’accéder aux informations de hiérarchie et d’élément relatives à la nouvelle sélection.

3. L’appel <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> et la transmission des éléments de la hiérarchie sélectionnés dans le `VSHPROPID_BrowseObject` paramètre remplit l' <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objet.

4. Un objet dérivé de l' [interface IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) est retourné pour [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) pour l’élément demandé, et l’environnement l’encapsule dans un <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (Voir l’étape suivante). Si l’appel échoue, l’environnement effectue un deuxième appel à `IVsHierarchy::GetProperty` , en lui transmettant le conteneur de sélection [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) que le ou les éléments de la hiérarchie fournissent.

    Le VSPackage de votre projet n’est pas créé <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , car le VSPackage de fenêtre fourni par l’environnement qui l’implémente (par exemple, **Explorateur de solutions**) construit <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> en son nom.

5. L’environnement appelle les méthodes de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> pour récupérer les objets en fonction de l' `IDispatch` interface à remplir dans la fenêtre **Propriétés** .

   Quand une valeur est modifiée dans la fenêtre **Propriétés** , les VSPackages implémentent `IVsTrackSelectionEx::OnElementValueChangeEx` et `IVsTrackSelectionEx::OnSelectionChangeEx` pour signaler la modification apportée à la valeur de l’élément. L’environnement appelle ensuite <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> ou <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> pour conserver les informations affichées dans la fenêtre **Propriétés** et les synchroniser avec les valeurs de propriété. Pour plus d’informations, consultez [mise à jour des valeurs de propriété dans la fenêtre Propriétés](#updating-property-values-in-the-properties-window).

   En plus de sélectionner un autre élément de projet dans **Explorateur de solutions** pour afficher les propriétés associées à cet élément, vous pouvez également choisir un autre objet dans un formulaire ou une fenêtre de document à l’aide de la liste déroulante disponible dans la fenêtre **Propriétés** . Pour plus d’informations, consultez Liste des objets de la [fenêtre Propriétés](../../extensibility/internals/properties-window-object-list.md).

   Vous pouvez modifier la façon dont les informations sont affichées dans la grille de la fenêtre **Propriétés** de l’ordre alphabétique à catégorie, et, si elles sont disponibles, vous pouvez également ouvrir une page de propriétés pour un objet sélectionné en cliquant sur les boutons appropriés dans la fenêtre **Propriétés** . Pour plus d’informations, consultez boutons et [pages](../../extensibility/internals/property-pages.md)de propriétés de la [fenêtre Propriétés](../../extensibility/internals/properties-window-buttons.md) .

   Enfin, le bas de la fenêtre **Propriétés** contient également une description du champ sélectionné dans la grille de la fenêtre **Propriétés** . Pour plus d’informations, consultez [obtention de descriptions de champs à partir de la fenêtre Propriétés](#getting-field-descriptions-from-the-properties-window).

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a> Mise à jour des valeurs de propriété dans la fenêtre Propriétés
Il existe deux façons de garantir la synchronisation de la fenêtre **Propriétés** avec les valeurs de propriété mises à jour. La première consiste à appeler l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>, qui donne accès aux fonctionnalités de base de fenêtrage, y compris l’utilisation et la création de fenêtres Outil et de document fournies par l’environnement. Les étapes qui suivent décrivent ce processus de synchronisation.

### <a name="updating-property-values-using-ivsuishell"></a>Mise à jour des valeurs de propriété à l’aide de l’interface IVsUIShell

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Pour mettre à jour les valeurs de propriété à l’aide de l’interface IVsUIShell

1. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (via le service <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>) quand un VSPackage, projet ou éditeur doit créer ou énumérer une fenêtre Outil ou de document.

2. Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> pour maintenir la synchronisation de la fenêtre **Propriétés** avec les modifications de propriété pour un projet (ou tout autre objet sélectionné qui est parcouru par la fenêtre **Propriétés** ) sans implémenter <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> et déclencher des <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> événements.

3. Implémentez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> pour activer ou désactiver, respectivement, la notification par le client des événements de la hiérarchie (cette hiérarchie n’a alors pas besoin d’implémenter <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>).

### <a name="updating-property-values-using-iconnection"></a>Mise à jour des valeurs de propriété à l’aide de l’interface IConnection
 La deuxième façon de garantir la synchronisation de la fenêtre **Propriétés** avec les valeurs de propriété mises à jour consiste à implémenter `IConnection` sur l’objet connectable pour indiquer l’existence des interfaces sortantes. Si vous souhaitez localiser le nom de propriété, dérivez votre objet de l’élément <xref:System.ComponentModel.ICustomTypeDescriptor>. L’implémentation de l’élément <xref:System.ComponentModel.ICustomTypeDescriptor> peut modifier les descripteurs de propriété renvoyés et modifier le nom d’une propriété. Pour localiser la description, créez un attribut dérivé de l’élément <xref:System.ComponentModel.DescriptionAttribute> et remplacez la propriété Description.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Considérations relatives à l’implémentation de l’interface IConnection

1. `IConnection` fournit l’accès à un sous-objet énumérateur avec l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. Elle fournit aussi l’accès à tous les sous-objets point de connexion, chacun d’eux implémentant l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>.

2. Chaque objet parcouru doit implémenter un événement <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>. La fenêtre **Propriétés** affiche des conseils sur l’événement défini via `IConnection`.

3. Un point de connexion détermine le nombre de connexions (une seule ou plusieurs) qu’il autorise dans son implémentation d’<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Un point de connexion autorisant une seule interface peut renvoyer <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> de la méthode <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>.

4. Un client peut appeler l’interface `IConnection` pour obtenir l’accès à un sous-objet énumérateur avec l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. L’interface <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> peut ensuite être appelée pour énumérer les points de connexion pour chaque ID d’interface sortante (IID).

5. L’interface `IConnection` peut également être appelée pour obtenir l’accès aux sous-objets point de connexion avec l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> pour chaque IID sortant. Par le biais de l' <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface, un client démarre ou termine une boucle consultative avec l’objet connectable et la propre synchronisation du client. Le client peut également appeler l' <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface pour obtenir un objet énumérateur avec l' <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> interface pour énumérer les connexions dont il a connaissance.

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a> Obtention de descriptions de champs à partir de la fenêtre Propriétés
En bas de la fenêtre **Propriétés** , une zone de description affiche des informations relatives au champ de propriété sélectionné. Cette fonctionnalité est activée par défaut. Si vous voulez masquer le champ de description, cliquez avec le bouton droit sur la fenêtre **Propriétés** et cliquez sur **Description**. Cette action supprime également la coche à côté du titre **Description** dans la fenêtre de menu. Vous pouvez afficher le champ à nouveau en suivant la même procédure pour réactiver **Description** .

 Les informations du champ de description proviennent de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Chaque méthode, interface, coclasse, etc. peut avoir un attribut `helpstring` non localisé dans la bibliothèque de types. La fenêtre **Propriétés** récupère la chaîne à partir de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> .

### <a name="to-specify-localized-help-strings"></a>Pour spécifier des chaînes d’aide localisées

1. Ajoutez l’attribut `helpstringdll` à l’instruction library dans la bibliothèque de types (`typelib`).

   > [!NOTE]
   > Cette étape est facultative si la bibliothèque de types se trouve dans un fichier de bibliothèque d’objets (.olb).

2. Spécifiez des attributs `helpstringcontext` pour les chaînes. Vous pouvez également spécifier des attributs `helpstring` .

    Ces attributs sont distincts des attributs `helpfile` et `helpcontext` qui sont contenus dans les vraies rubriques d’aide du fichier .chm.

   Pour récupérer les informations de description à afficher pour le nom de la propriété en surbrillance, la fenêtre **Propriétés** appelle <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> pour la propriété qui est sélectionnée, en spécifiant l' `lcid` attribut souhaité pour la chaîne de sortie. En interne, <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> recherche le fichier .dll spécifié dans l’attribut `helpstringdll` et appelle `DLLGetDocumentation` sur ce fichier .dll avec le contexte spécifié et l’attribut `lcid`.

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
