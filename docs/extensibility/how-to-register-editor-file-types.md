---
title: "Comment : enregistrer des Types de fichiers de l&#39;&#233;diteur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités - inscrire des types de fichiers"
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Comment : enregistrer des Types de fichiers de l&#39;&#233;diteur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La façon la plus facile d'enregistrer les types de fichier de l'éditeur est en utilisant des attributs d'alignement fournis en tant que partie des classes managées en [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] \(MPF\) du package.  Si vous implémentez votre package dans le natif [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)], vous pouvez également écrire un script de Registre qui stocke votre éditeur et les extensions associées.  
  
## Alignement utilisation des classes de MPF  
  
#### Pour enregistrer les types de fichier de l'éditeur utilisation des classes de MPF  
  
1.  fournissez à la classe d' <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> les paramètres appropriés pour votre éditeur dans la classe de votre VSPackage.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Où « . L'exemple » est l'extension stockées pour cet éditeur, et « 32 " est son niveau de priorité.  
  
     `projectGuid` est un GUID pour divers types de fichier, défini dans <xref:Microsoft.VisualStudio.VSConstants.CLSID_MiscellaneousFilesProject>.  Le dossier fichiers divers de type de fichier est fourni, afin que le fichier résultant n'affiche pas être une partie du processus de génération.  
  
     `TemplateDir` représente le dossier qui contient les fichiers modèles qui sont inclus dans l'exemple de base managé d'éditeur.  
  
     `NameResourceID` est défini dans le fichier de Resources.h du projet de BasicEditorUI, et identifie l'éditeur en tant que « mon éditeur ».  
  
2.  Remplacez la méthode <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     Dans votre implémentation de la méthode d' <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> , appelez la méthode d' <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> et passez l'instance de votre fabrique de l'éditeur comme indiqué ci\-dessous.  
  
    ```  
    protected override void Initialize()  
    {  
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,   
        "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
           //Create Editor Factory  
        editorFactory = new EditorFactory(this);  
        base.RegisterEditorFactory(editorFactory);  
    }  
    ```  
  
     Cette étape inscrit la fabrique d'éditeur et les extensions de fichier de l'éditeur.  
  
3.  Désinscrivez les fabriques d'éditeur.  
  
     Les fabriques d'éditeur sont automatiquement annulées l'enregistrement lorsque le VSPackage est supprimé.  Si l'objet de fabrique d'éditeur implémente l'interface d' <xref:System.IDisposable> , sa méthode d' `Dispose` est appelée après la fabrique a été annulée l'enregistrement à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Inscription à l'aide d'un script de Registre  
 Stocker les fabriques et les types de fichier de l'éditeur dans le natif [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] s'effectue en utilisant un script de Registre pour écrire dans les fenêtres le Registre, comme illustré par le suivant.  
  
#### Pour enregistrer les types de fichier de l'éditeur à l'aide d'un script de Registre  
  
1.  Dans votre script de Registre, définissez la fabrique d'éditeur et la chaîne GUID de fabrique d'éditeur comme indiqué dans la section d' `GUID_BscEditorFactory` du script suivant de Registre.  en outre, définissez l'extension et la priorité de l'extension d'éditeur :  
  
    ```  
  
                NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions             {                 val rtf = d 50             }  
        }  
    }  
    ```  
  
     L'extension de fichier de l'éditeur dans cet exemple est identifiée comme « .rtf » et sa priorité est « 50 ".  Les chaînes du GUID sont définies dans le fichier Resource.h de l'exemple de projet de BscEdit.  
  
2.  enregistrez le VSPackage.  
  
3.  Inscription de la fabrique d'éditeur.  
  
     La fabrique d'éditeur est stockée dans l'implémentation d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> .  
  
    ```  
    // create editor factory.  
    if (m_srpEdFact == NULL)   
    {  
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;  
        if (NULL == pEdFact)  
          return E_OUTOFMEMORY;  
  
        if (!pEdFact->FInit(this))  
          return E_UNEXPECTED;  
  
        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()  
    }  
    // Query service for IVsRegisterEditors, register the editor factory  
    CComPtr<IVsRegisterEditors> srpRegEd;  
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))  
      {  
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));  
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,  
                      m_srpEdFact, &m_dwEditorCookie)))   
          {  
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));  
            return E_FAIL;  
          }  
      }  
        return S_OK;  
    }  
    ```  
  
     Les chaînes du GUID sont définies dans le fichier Resource.h du projet de BscEdit.