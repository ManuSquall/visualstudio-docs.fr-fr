---
title: Adaptation de l’éditeur de Code hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdc507e3897398e47ed8038fa28165eb4add166c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313575"
---
# <a name="adapt-legacy-code-to-the-editor"></a>Adapter le code hérité vers l’éditeur
L’éditeur Visual Studio propose de nombreuses fonctionnalités que vous pouvez accéder depuis les composants de code existants. Les instructions suivantes indiquent comment adapter un composant non MEF, par exemple, un VSPackage pour utiliser les fonctionnalités de l’éditeur. Les instructions indiquent également comment utiliser des adaptateurs pour obtenir les services de l’éditeur de code managé et non managé.

## <a name="editor-adapters"></a>Adaptateurs de l’éditeur
Adaptateurs de l’éditeur, ou des shims, sont des wrappers pour les objets de l’éditeur qui exposent également les classes et interfaces dans les <xref:Microsoft.VisualStudio.TextManager.Interop> API. Vous pouvez utiliser les adaptateurs pour vous déplacer entre les services non éditeur par exemple, commandes d’interpréteur de commandes de Visual Studio et les services de l’éditeur. (C’est la façon dont l’éditeur est actuellement hébergé dans Visual Studio.) Les adaptateurs permettent également l’éditeur et la langue service les extensions héritées à fonctionner correctement dans Visual Studio.

## <a name="use-editor-adapters"></a>Utilisation des adaptateurs de l’éditeur
Le <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> fournit des méthodes qui basculent entre les nouvelles interfaces de l’éditeur et les interfaces héritées, ainsi que les méthodes qui créent des adaptateurs.

Si vous utilisez ce service dans un composant MEF, vous pouvez importer le service comme suit.

```
[Import(typeof(IVsEditorAdaptersFactoryService))]
internal IVsEditorAdaptersFactoryService editorFactory;
```

Si vous souhaitez utiliser ce service dans un composant non MEF, suivez les instructions dans la section « À l’aide de Visual Studio Editor Services dans un Non-MEF composant » plus loin dans cette rubrique.

## <a name="switch-between-the-new-editor-api-and-the-legacy-api"></a>Basculer entre la nouvelle API de l’éditeur et l’API héritée
Utiliser les méthodes suivantes pour basculer entre un objet de l’éditeur et une interface héritée.

|Méthode|Conversion|
|------------|----------------|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Convertit un <xref:Microsoft.VisualStudio.Text.ITextBuffer> à un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Convertit un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> à un <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Convertit un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> à un <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Convertit un <xref:Microsoft.VisualStudio.Text.Editor.ITextView> à un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Convertit un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> à un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|

## <a name="create-adapters"></a>Créer des adaptateurs
Utiliser les méthodes suivantes pour créer des adaptateurs pour les interfaces héritées.

|Méthode|Conversion|
|------------|----------------|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Crée un objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Crée un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> spécifié <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Crée un objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Crée un objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Crée un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Crée un objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|

## <a name="creating-adapters-in-unmanaged-code"></a>Création d’adaptateurs en code non managé
Toutes les classes d’adaptateur sont inscrits pour être local hébergé qui peut être créé et peut être instancié à l’aide de la `VsLocalCreateInstance()` (fonction).

Toutes les cartes sont créés à l’aide de GUID qui sont définies dans le *vsshlids.h* de fichiers dans le *\..\VisualStudioIntegration\Common\Inc\\* dossier du SDK Visual Studio installation. Pour créer une instance de VsTextBufferAdapter, utilisez le code suivant.

```
IVsTextBuffer *pBuf = NULL;
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);
```

## <a name="create-adapters-in-managed-code"></a>Créer des cartes en code managé
Dans le code managé, vous pouvez co-créer les cartes de la même façon que celle décrite pour le code non managé. Vous pouvez également utiliser un service MEF qui vous permet de créer et interagir avec les adaptateurs. Cette manière d’obtenir un adaptateur permet un contrôle plus précis que vous avez lorsque vous la créez conjointement.

### <a name="to-create-an-adapter-for-ivstextview"></a>Pour créer un adaptateur pour IVsTextView

1. Ajoutez une référence à *Microsoft.VisualStudio.Editor.dll*. Assurez-vous que l’option `CopyLocal` est défini sur `false`.

2. Instanciez le <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, comme suit.

    ```
    using Microsoft.VisualStudio.Editor;
    ...
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();
    ```

3. Appelez la méthode `CreateX()`.

    ```
    adapterFactoryService.CreateTextViewAdapter(textView);
    ```

## <a name="use-the-visual-studio-editor-directly-from-unmanaged-code"></a>Utilisez l’éditeur Visual Studio directement à partir de code non managé
L’espace de noms Microsoft.VisualStudio.Platform.VSEditor et l’espace de noms Microsoft.VisualStudio.Platform.VSEditor.Interop exposent les interfaces COM-callable en tant qu’interfaces de IVx. Par exemple, l’interface Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer est la version COM de le <xref:Microsoft.VisualStudio.Text.ITextBuffer> interface. À partir de la `IVxTextBuffer`, vous pouvez accéder aux instantanés de la mémoire tampon, modifier la mémoire tampon, écouter des événements de modification du texte sur la mémoire tampon et créer des points de suivi et d’intervalles. Les étapes suivantes montrent comment accéder à un `IVxTextBuffer` à partir d’un `IVsTextBuffer`.

### <a name="to-get-an-ivxtextbuffer"></a>Pour obtenir une IVxTextBuffer

1. Les définitions pour le IVx\* sont des interfaces dans les *VSEditor.h* de fichiers dans le *\..\VisualStudioIntegration\Common\Inc\\* dossier de Visual Studio Installation du Kit de développement logiciel.

2. Le code suivant instancie une mémoire tampon de texte à l’aide de la `IVsUserData->GetData()` (méthode). Dans le code suivant, `pData` est un pointeur vers un `IVsUserData` objet.

    ```cpp
    #include <textmgr.h>
    #include <VSEditor.h>
    #include <vsshlids.h>

    CComPtr<IVsTextBuffer> pVsTextBuffer;
    CComPtr<IVsUserData> pData;
    CComPtr<IVxTextBuffer> pVxBuffer;
    ...
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))
    {
        CComVariant vt;
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))
        {
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);
        }
    }
    ```

## <a name="use-visual-studio-editor-services-in-a-non-mef-component"></a>Utiliser les services de l’éditeur Visual Studio dans un composant non MEF
Si vous avez un composant de code managé existant qui n’utilise pas de MEF et que vous souhaitez utiliser les services de l’éditeur Visual Studio, vous devez ajouter une référence à l’assembly qui contient le ComponentModelHost VSPackage et obtenir son service SComponentModel en vue.

### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>Pour consommer des composants de l’éditeur Visual Studio à partir d’un composant non MEF

1. Ajoutez une référence à la *Microsoft.VisualStudio.ComponentModelHost.dll* assembly dans le *\..\Common7\IDE\\* dossier de l’installation de Visual Studio. Assurez-vous que l’option `CopyLocal` est défini sur `false`.

2. Ajouter une privée `IComponentModel` membre à la classe dans laquelle vous souhaitez utiliser les services de l’éditeur de Visual Studio, comme suit.

    ```
    using Microsoft.VisualStudio.ComponentModelHost;
    ....
    private IComponentModel componentModel;
    ```

3. Instanciez le modèle de composant dans la méthode d’initialisation pour votre composant.

    ```
    componentModel =
        (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));
    ```

4. Après cela, vous pouvez obtenir l’un des services de l’éditeur Visual Studio en appelant le `IComponentModel.GetService<T>()` méthode pour le service souhaité.

    ```
    textBufferFactoryService =
        componentModel.GetService<ITextBufferFactoryService>();
    ```
