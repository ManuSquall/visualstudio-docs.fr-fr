---
title: Adaptation du code hérité à l’éditeur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb90723a72c10dbf6cfda5edd4aa68f71f1c6b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184922"
---
# <a name="adapting-legacy-code-to-the-editor"></a>Adaptation du code hérité dans l’éditeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’éditeur Visual Studio propose de nombreuses fonctionnalités auxquelles vous pouvez accéder à partir de composants de code existants. Les instructions suivantes indiquent comment adapter un composant non MEF, par exemple un VSPackage, pour consommer les fonctionnalités de l’éditeur. Les instructions montrent également comment utiliser des adaptateurs pour obtenir les services de l’éditeur dans du code managé et non managé.  
  
## <a name="editor-adapters"></a>Adaptateurs de l’éditeur  
 Les adaptateurs d’éditeur, ou shims, sont des wrappers pour les objets Editor qui exposent également les classes et les interfaces dans l' <xref:Microsoft.VisualStudio.TextManager.Interop> API. Vous pouvez utiliser les adaptateurs pour vous déplacer entre les services non-éditeur, par exemple, les commandes de l’interpréteur de commandes Visual Studio et les services de l’éditeur. (Il s’agit de la façon dont l’éditeur est actuellement hébergé dans Visual Studio.) Les adaptateurs activent également l’éditeur hérité et les extensions du service de langage pour fonctionner correctement dans Visual Studio.  
  
## <a name="using-editor-adapters"></a>Utilisation d’adaptateurs d’éditeur  
 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>Fournit des méthodes qui basculent entre les nouvelles interfaces d’éditeur et les interfaces héritées, ainsi que les méthodes qui créent des adaptateurs.  
  
 Si vous utilisez ce service dans une partie du composant MEF, vous pouvez importer le service comme suit.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Si vous souhaitez utiliser ce service dans un composant non MEF, suivez les instructions de la section « utilisation des services de l’éditeur Visual Studio dans un composant non MEF » plus loin dans cette rubrique.  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>Basculement entre la nouvelle API d’éditeur et l’API héritée  
 Utilisez les méthodes suivantes pour basculer entre un objet Editor et une interface héritée.  
  
|Méthode|Conversion|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Convertit un <xref:Microsoft.VisualStudio.Text.ITextBuffer> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Convertit un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> en <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Convertit un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> en <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Convertit un <xref:Microsoft.VisualStudio.Text.Editor.ITextView> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Convertit un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> en <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
  
## <a name="creating-adapters"></a>Création d'adaptateurs  
 Utilisez les méthodes suivantes pour créer des adaptateurs pour les interfaces héritées.  
  
|Méthode|Conversion|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Crée un objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Crée un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> pour un spécifié <xref:Microsoft.VisualStudio.Utilities.IContentType> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Crée un objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Crée un objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Crée un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> pour un <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Crée un objet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>Création d’adaptateurs dans du code non managé  
 Toutes les classes d’adaptateur sont inscrites pour être cocréées localement et peuvent être instanciées à l’aide de la `VsLocalCreateInstance()` fonction.  
  
 Tous les adaptateurs sont créés à l’aide des GUID définis dans le fichier vsshlids. h dans le. Dossier \VisualStudioIntegration\Common\Inc\ de l’installation du kit de développement logiciel (SDK) Visual Studio. Pour créer une instance de VsTextBufferAdapter, utilisez le code suivant.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>Création d’adaptateurs dans du code managé  
 En code managé, vous pouvez co-créer les adaptateurs de la même façon que pour le code non managé. Vous pouvez également utiliser un service MEF qui vous permet de créer des adaptateurs et d’interagir avec eux. Cette méthode d’obtention d’un adaptateur permet un contrôle plus précis que celui que vous avez lorsque vous le créez.  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>Pour créer un adaptateur pour IVsTextView  
  
1. Ajoutez une référence à Microsoft.VisualStudio.Editor.dll. Assurez-vous que la valeur `CopyLocal` est définie sur `false`.  
  
2. Instanciez le <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , comme suit.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3. Appelez la méthode `CreateX()` .  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>Utilisation de l’éditeur Visual Studio directement à partir de code non managé  
 L’espace de noms Microsoft. VisualStudio. Platform. VSEditor et l’espace de noms Microsoft. VisualStudio. Platform. VSEditor. Interop exposent les interfaces pouvant être appelées par COM en tant qu’interfaces IVx *. Par exemple, l’interface Microsoft. VisualStudio. Platform. VSEditor. Interop. IVxTextBuffer est la version COM de l' <xref:Microsoft.VisualStudio.Text.ITextBuffer> interface. À partir du `IVxTextBuffer` , vous pouvez accéder aux instantanés de la mémoire tampon, modifier la mémoire tampon, écouter les événements de modification de texte sur la mémoire tampon et créer des points de suivi et des étendues. Les étapes suivantes montrent comment accéder à un `IVxTextBuffer` à partir d’un `IVsTextBuffer` .  
  
#### <a name="to-get-an-ivxtextbuffer"></a>Pour recevoir un IVxTextBuffer  
  
1. Les définitions des interfaces IVx * se trouvent dans le fichier VSEditor. h dans le. Dossier \VisualStudioIntegration\Common\Inc\ de l’installation du kit de développement logiciel (SDK) Visual Studio.  
  
2. Le code suivant instancie une mémoire tampon de texte à l’aide de la `IVsUserData->GetData()` méthode. Dans le code suivant, `pData` est un pointeur vers un `IVsUserData` objet.  
  
    ```  
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
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>Utilisation des services de l’éditeur Visual Studio dans un composant non MEF  
 Si vous disposez d’un composant de code managé existant qui n’utilise pas MEF et que vous souhaitez utiliser les services de l’éditeur Visual Studio, vous devez ajouter une référence à l’assembly qui contient le VSPackage ComponentModelHost et obtenir son service SComponentModel.  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>Pour utiliser les composants de l’éditeur Visual Studio à partir d’un composant non MEF  
  
1. Ajoutez une référence à l’assembly Microsoft.VisualStudio.ComponentModelHost.dll dans le.. Dossier \Common7\IDE\ de l’installation de Visual Studio. Assurez-vous que la valeur `CopyLocal` est définie sur `false`.  
  
2. Ajoutez un `IComponentModel` membre privé à la classe dans laquelle vous souhaitez utiliser les services de l’éditeur Visual Studio, comme suit.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3. Instanciez le modèle de composant dans la méthode d’initialisation de votre composant.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4. Après cela, vous pouvez obtenir l’un des services de l’éditeur Visual Studio en appelant la `IComponentModel.GetService<T>()` méthode pour le service souhaité.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```
