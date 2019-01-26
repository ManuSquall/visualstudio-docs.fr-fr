---
title: 'Procédure : Inscrire des Types de fichiers de l’éditeur | Microsoft Docs'
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f26b7421676081b32060dd4f342ee05098d90a7c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54980321"
---
# <a name="how-to-register-editor-file-types"></a>Procédure : Inscrire des types de fichiers de l’éditeur
Le moyen le plus simple pour inscrire les types de fichiers de l’éditeur est à l’aide des attributs d’inscription fournis dans le cadre de la [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] package framework (MPF) classes managées. Si vous implémentez votre package en mode natif [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], vous pouvez également écrire un script de Registre qui inscrit votre éditeur et les extensions associées.

## <a name="registration-using-mpf-classes"></a>Inscription à l’aide des classes MPF

### <a name="to-register-editor-file-types-using-mpf-classes"></a>Pour inscrire des types de fichiers de l’éditeur à l’aide des classes MPF

1. Fournir la <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> classe avec les paramètres appropriés pour votre éditeur dans la classe de votre VSPackage.

   ```
   [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,
        ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",
        TemplateDir = "..\\..\\Templates",
        NameResourceID = 106)]
   ```

    Où *. Exemple* est l’extension qui est inscrit pour cet éditeur, et « 32 » est son niveau de priorité.

    Le `projectGuid` est le GUID pour les types de fichier divers, définis dans <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid>. Le type de fichier divers est fourni, afin que le fichier résultant ne va pas faire partie du processus de génération.

    *TemplateDir* représente le dossier qui contient les fichiers de modèle qui sont inclus dans l’exemple d’éditeur de base managé.

    `NameResourceID` est défini dans le *Resources.h* fichier du projet BasicEditorUI et identifie l’éditeur en tant que « Mes éditeur ».

2. Remplacez la méthode <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .

    Dans votre implémentation de la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> méthode, appelez le <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> méthode et passe l’instance de votre fabrique d’éditeur comme illustré ci-dessous.

   ```csharp
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

3. Annuler l’inscription de fabriques d’éditeur.

    Fabriques d’éditeur sont automatiquement annulées lorsque le VSPackage est supprimé. Si l’objet de fabrique d’éditeur implémente le <xref:System.IDisposable> interface, son `Dispose` méthode est appelée une fois la fabrique a été annulée avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="registration-using-a-registry-script"></a>Inscription à l’aide d’un script de Registre
 L’inscription des types de fichiers et les fabriques d’éditeur en mode natif [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] s’effectue à l’aide d’un script de Registre à écrire dans le Registre windows, comme illustré ci-après.

### <a name="to-register-editor-file-types-using-a-registry-script"></a>Pour inscrire des types de fichiers de l’éditeur à l’aide d’un script de Registre

1.  Dans votre script de Registre, définissez la fabrique d’éditeur et de la fabrique d’éditeur chaîne GUID comme indiqué dans la `GUID_BscEditorFactory` section du script de Registre suivant. En outre, définissez l’extension et la priorité de l’extension de l’éditeur :

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

     L’extension de fichier de l’éditeur dans cet exemple est identifiée en tant que *.rtf* et sa priorité est « 50 ». Les chaînes GUID sont définies dans *Resource.h* fichier de l’exemple de projet BscEdit.

2.  Inscrivez le VSPackage.

3.  Inscrire la fabrique d’éditeur.

     La fabrique d’éditeur est inscrit dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> implémentation.

    ```cpp
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

     Les chaînes GUID sont définies dans *Resource.h* fichier du projet BscEdit.