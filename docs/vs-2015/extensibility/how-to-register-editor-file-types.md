---
title: 'Comment : enregistrer les types de fichiers de l’éditeur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d22e61d88b5f6e3959a369f6957efbc824384b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204119"
---
# <a name="how-to-register-editor-file-types"></a>Guide pratique pour inscrire des types de fichiers d’éditeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le moyen le plus simple d’enregistrer les types de fichiers de l’éditeur consiste à utiliser les attributs d’inscription fournis dans le cadre des [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] classes Managed package Framework (MPF). Si vous implémentez votre package en mode natif [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , vous pouvez également écrire un script de Registre qui inscrit votre éditeur et les extensions associées.  
  
## <a name="registration-using-mpf-classes"></a>Inscription à l’aide des classes MPF  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>Pour enregistrer les types de fichiers de l’éditeur à l’aide des classes MPF  
  
1. Fournissez la <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> classe avec les paramètres appropriés pour votre éditeur dans la classe de votre VSPackage.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Où». Sample» est l’extension qui est inscrite pour cet éditeur et « 32 » est son niveau de priorité.  
  
     `projectGuid`Est le GUID pour les divers types de fichiers, défini dans <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid> . Le type de fichier divers est fourni, de sorte que le fichier résultant ne fera pas partie du processus de génération.  
  
     `TemplateDir` représente le dossier qui contient les fichiers de modèle inclus avec l’exemple de l’éditeur de base managé.  
  
     `NameResourceID` est défini dans le fichier Resources. h du projet BasicEditorUI et identifie l’éditeur comme « mon éditeur ».  
  
2. Remplacez la méthode <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .  
  
     Dans votre implémentation de la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode, appelez la <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> méthode et transmettez l’instance de votre fabrique d’éditeur comme illustré ci-dessous.  
  
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
  
     Cette étape inscrit la fabrique d’éditeur et les extensions de fichier de l’éditeur.  
  
3. Annulez l’inscription des fabriques d’éditeur.  
  
     Les fabriques d’éditeur sont désinscrites automatiquement lorsque le VSPackage est supprimé. Si l’objet de fabrique d’éditeur implémente l' <xref:System.IDisposable> interface, sa `Dispose` méthode est appelée après l’annulation de l’inscription de la fabrique [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="registration-using-a-registry-script"></a>Inscription à l’aide d’un script de Registre  
 L’inscription des fabriques d’éditeur et des types de fichiers en mode natif [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] s’effectue à l’aide d’un script de Registre pour écrire dans le Registre Windows, comme illustré ci-dessous.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>Pour inscrire des types de fichiers de l’éditeur à l’aide d’un script de Registre  
  
1. Dans votre script de Registre, définissez la fabrique d’éditeur et la chaîne GUID de la fabrique d’éditeur, comme indiqué dans la `GUID_BscEditorFactory` section du script de Registre suivant. Définissez également l’extension et la priorité de l’extension de l’éditeur :  
  
    ```  
  
          NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions            {                val rtf = d 50            }  
        }  
    }  
    ```  
  
     L’extension de fichier de l’éditeur dans cet exemple est identifiée en tant que « . rtf » et sa priorité est « 50 ». Les chaînes GUID sont définies dans le fichier Resource. h de l’exemple de projet BscEdit.  
  
2. Inscrivez le VSPackage.  
  
3. Inscrire la fabrique d’éditeur.  
  
     La fabrique d’éditeur est inscrite dans l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> implémentation de.  
  
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
  
     Les chaînes GUID sont définies dans le fichier Resource. h du projet BscEdit.
