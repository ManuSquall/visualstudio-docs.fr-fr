---
title: L’inscription d’un langage hérité1 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e473df78787b83655c402bae666448e718216b36
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769594"
---
# <a name="registering-a-legacy-language-service"></a>L’inscription d’un Service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dans l’infrastructure de package managé (MPF), le service de langage est offert par un VSPackage (consultez [VSPackages](../../extensibility/internals/vspackages.md)) et est enregistré avec [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en ajoutant des entrées et clés de Registre. Ce processus d’inscription est effectué partiellement lors de l’installation et en partie lors de l’exécution.  
  
## <a name="register-the-language-service-by-using-attributes"></a>Inscrire le Service de langage à l’aide d’attributs  
 Les attributs suivants sont utilisés pour inscrire un service de langage.  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>  
  
  Ces attributs sont expliquées ci-dessous  
  
### <a name="provideserviceattribute"></a>ProvideServiceAttribute  
 Cet attribut inscrit votre service de langage en tant que service.  
  
### <a name="example"></a>Exemple  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideServiceAttribute(typeof(TestLanguageService),  
                             ServiceName = "Test Language Service")]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageserviceattribute"></a>ProvideLanguageServiceAttribute  
 Cet attribut inscrit votre service de langage spécifiquement comme un service de langage. Il vous permet de définir des options qui spécifient les fonctionnalités offertes par votre service de langage. L’exemple montre un sous-ensemble des options de qu'un service de langage peut fournir. Pour l’ensemble complet des options de service de langage, consultez <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>.  
  
### <a name="example"></a>Exemple  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageServiceAttribute(typeof(TestLanguageService),  
                             "Test Language",  
                             106,             // resource ID of localized language name  
                             CodeSense = true,             // Supports IntelliSense  
                             RequestStockColors = false,   // Supplies custom colors  
                             EnableCommenting = true,      // Supports commenting out code  
                             EnableAsyncCompletion = true  // Supports background parsing  
                             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageextensionattribute"></a>ProvideLanguageExtensionAttribute  
 Cet attribut associe votre service de langage avec une extension de fichier. Chaque fois qu’un fichier avec cette extension est chargé, dans n’importe quel projet, votre service de langage est démarré et utilisé pour afficher le contenu du fichier.  
  
### <a name="example"></a>Exemple  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageExtensionAttribute(typeof(TestLanguageService),  
                                       ".Testext")]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguagecodeexpansionattribute"></a>ProvideLanguageCodeExpansionAttribute  
 Cet attribut enregistre un emplacement à partir de quel code des modèles d’extension ou extrait de code sont obtenues. Ces informations sont utilisées par le **navigateur d’extraits de Code** et par l’éditeur lorsqu’un extrait de code est inséré dans le fichier source.  
  
### <a name="example"></a>Exemple  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageCodeExpansionAttribute(  
             typeof(TestLanguageService),  
             "Test Language", // Name of language used as registry key.  
             106,           // Resource ID of localized name of language service.  
             "testlanguage",  // language key used in snippet templates.  
             @"%InstallRoot%\Test Language\SnippetsIndex.xml",  // Path to snippets index  
             SearchPaths = @"%InstallRoot%\Test Language\Snippets\%LCID%\Snippets\;" +  
                           @"%TestDocs%\Code Snippets\Test Language\Test Code Snippets"  
             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
### <a name="providelanguageeditoroptionpageattribute"></a>ProvideLanguageEditorOptionPageAttribute  
 Cet attribut inscrit une page de propriétés à afficher dans le **Options** boîte de dialogue sous la **éditeur de texte** catégorie. Utilisez une de ces attributs pour chaque page à afficher pour votre service de langage. Si vous avez besoin organiser vos pages dans une structure arborescente, utilisez des attributs supplémentaires pour définir chaque nœud de l’arborescence.  
  
### <a name="example"></a>Exemple  
 Cet exemple montre deux pages de propriétés, **Options** et **Indenting**, ainsi qu’un nœud qui contient la deuxième page de propriétés.  
  
```csharp  
using Microsoft.VisualStudio.Shell;  
  
namespace TestLanguagePackage  
{  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             "Options",      // Registry key name for property page  
             "#242",         // Localized name of property page  
             OptionPageGuid = "{A2FE74E1-FFFF-3311-4342-123052450768}"  // GUID of property page  
             )]  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             "Advanced",     // Registry key name for node  
             "#243",         // Localized name of node  
             )]  
    [ProvideLanguageEditorOptionPageAttribute(  
             "Test Language",  // Registry key name for language  
             @"Advanced\Indenting",     // Registry key name for property page  
             "#244",         // Localized name of property page  
             OptionPageGuid = "{A2FE74E2-FFFF-3311-4342-123052450768}"  // GUID of property page  
             )]  
  
    public class TestLanguagePackage : Package  
    {  
    }  
}  
```  
  
## <a name="proffer-the-language-service-at-runtime"></a>Offrir le Service de langage lors de l’exécution  
 Lors du chargement de votre package de langue, vous devez indiquer à [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] que votre service de langage est prêt. Pour cela, vous devez proffering le service. Cette opération est effectuée le <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> (méthode). En outre, vous devez démarrer une minuterie qui appelle votre service de langage pendant les périodes d’inactivité de sorte que l’analyse d’arrière-plan peut être effectuée. Cette minuterie d’inactivité est également utilisée pour mettre à jour les propriétés du document si vous avez implémenté un via le <xref:Microsoft.VisualStudio.Package.DocumentProperties> classe. Pour prendre en charge un minuteur, votre package doit implémenter le <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> interface (uniquement la <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> méthode doit être entièrement implémentée ; les méthodes restantes peuvent retourner des valeurs par défaut).  
  
### <a name="example"></a>Exemple  
 Cet exemple montre une approche courante pour proffering un service et en fournissant une minuterie d’inactivité.  
  
```csharp  
  
using System;  
using System.Runtime.InteropServices;  
using System.ComponentModel.Design;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.Shell;  
using Microsoft.VisualStudio.OLE.Interop;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    [Microsoft.VisualStudio.Shell.ProvideService(typeof(TestLanguageService))]  
    [Microsoft.VisualStudio.Shell.ProvideLanguageExtension(typeof(TestLanguageService), ".testext")]  
    [Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(TestLanguageService), "Test Language", 0,  
        AutoOutlining = true,  
        EnableCommenting = true,  
        MatchBraces = true,  
        ShowMatchingBrace = true)]  
    [Guid("00000000-0000-0000-0000-00000000000")] //provide a unique GUID for the package  
  
    public class TestLanguagePackage : Package, IOleComponent  
    {  
        private uint m_componentID;  
  
        protected override void Initialize()  
        {  
            base.Initialize();  // required  
  
            // Proffer the service.  
            IServiceContainer serviceContainer = this as IServiceContainer;  
            TestLanguageService langService      = new TestLanguageService();  
            langService.SetSite(this);  
            serviceContainer.AddService(typeof(TestLanguageService),  
                                        langService,  
                                        true);  
  
            // Register a timer to call our language service during  
            // idle periods.  
            IOleComponentManager mgr = GetService(typeof(SOleComponentManager))  
                                       as IOleComponentManager;  
            if (m_componentID == 0 && mgr != null)  
            {  
                OLECRINFO[] crinfo = new OLECRINFO[1];  
                crinfo[0].cbSize            = (uint)Marshal.SizeOf(typeof(OLECRINFO));  
                crinfo[0].grfcrf            = (uint)_OLECRF.olecrfNeedIdleTime |  
                                              (uint)_OLECRF.olecrfNeedPeriodicIdleTime;  
                crinfo[0].grfcadvf          = (uint)_OLECADVF.olecadvfModal     |  
                                              (uint)_OLECADVF.olecadvfRedrawOff |  
                                              (uint)_OLECADVF.olecadvfWarningsOff;  
                crinfo[0].uIdleTimeInterval = 1000;  
                int hr = mgr.FRegisterComponent(this, crinfo, out m_componentID);  
            }  
        }  
  
        protected override void Dispose(bool disposing)  
        {  
            if (m_componentID != 0)  
            {  
                IOleComponentManager mgr = GetService(typeof(SOleComponentManager))  
                                           as IOleComponentManager;  
                if (mgr != null)  
                {  
                    int hr = mgr.FRevokeComponent(m_componentID);  
                }  
                m_componentID = 0;  
            }  
  
            base.Dispose(disposing);  
        }  
  
        #region IOleComponent Members  
  
        public int FDoIdle(uint grfidlef)  
        {  
            bool bPeriodic = (grfidlef & (uint)_OLEIDLEF.oleidlefPeriodic) != 0;  
            // Use typeof(TestLanguageService) because we need to  
            // reference the GUID for our language service.  
            LanguageService service = GetService(typeof(TestLanguageService))  
                                      as LanguageService;  
            if (service != null)  
            {  
                service.OnIdle(bPeriodic);  
            }  
            return 0;  
        }  
  
        public int FContinueMessageLoop(uint uReason,  
                                        IntPtr pvLoopData,  
                                        MSG[] pMsgPeeked)  
        {  
            return 1;  
        }  
  
        public int FPreTranslateMessage(MSG[] pMsg)  
        {  
            return 0;  
        }  
  
        public int FQueryTerminate(int fPromptUser)  
        {  
            return 1;  
        }  
  
        public int FReserved1(uint dwReserved,  
                              uint message,  
                              IntPtr wParam,  
                              IntPtr lParam)  
        {  
            return 1;  
        }  
  
        public IntPtr HwndGetWindow(uint dwWhich, uint dwReserved)  
        {  
            return IntPtr.Zero;  
        }  
  
        public void OnActivationChange(IOleComponent pic,  
                                       int fSameComponent,  
                                       OLECRINFO[] pcrinfo,  
                                       int fHostIsActivating,  
                                       OLECHOSTINFO[] pchostinfo,  
                                       uint dwReserved)  
        {  
        }  
  
        public void OnAppActivate(int fActive, uint dwOtherThreadID)  
        {  
        }  
  
        public void OnEnterState(uint uStateID, int fEnter)  
        {  
        }  
  
        public void OnLoseActivation()  
        {  
        }  
  
        public void Terminate()  
        {  
        }  
  
        #endregion  
    }  
}   
```

