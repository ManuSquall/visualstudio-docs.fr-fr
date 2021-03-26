---
title: Inscription d’un Service1 de langage hérité | Microsoft Docs
description: En savoir plus sur l’inscription d’un service de langage hérité à partir d’un VSPackage avec Visual Studio en ajoutant des clés et des entrées de registre.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d5fa94fbd514e5fb162bc569438197dd8c65444b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060768"
---
# <a name="registering-a-legacy-language-service-1"></a>Inscription d’un service de langage hérité 1
Dans Managed package Framework (MPF), le service de langage est offerts par un VSPackage (voir [VSPackages](../../extensibility/internals/vspackages.md)) et est inscrit auprès de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en ajoutant des clés et des entrées de registre. Ce processus d’inscription s’effectue en partie pendant l’installation et en partie au moment de l’exécution.

## <a name="register-the-language-service-by-using-attributes"></a>Inscrire le service de langage à l’aide d’attributs
 Les attributs suivants sont utilisés pour inscrire un service de langage.

- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>

  Ces attributs sont expliqués ci-dessous

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
 Cet attribut inscrit votre service de langage spécifiquement en tant que service de langage. Elle vous permet de définir des options qui spécifient les fonctionnalités offertes par votre service de langage. L’exemple montre un sous-ensemble des options que le service de langage peut fournir. Pour obtenir l’ensemble complet des options du service de langage, consultez <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> .

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
 Cet attribut associe votre service de langage à une extension de fichier. Chaque fois qu’un fichier avec cette extension est chargé, dans n’importe quel projet, votre service de langage est démarré et utilisé pour afficher le contenu du fichier.

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
 Cet attribut inscrit un emplacement à partir duquel les modèles d’expansion ou d’extrait de code sont obtenus. Ces informations sont utilisées par le **navigateur des extraits de code** et par l’éditeur lorsqu’un extrait de code est inséré dans le fichier source.

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
 Cet attribut inscrit une page de propriétés à afficher dans la boîte de dialogue **options** sous la catégorie **éditeur de texte** . Utilisez l’un de ces attributs pour chaque page à afficher pour votre service de langage. Si vous avez besoin d’organiser vos pages dans une arborescence, utilisez des attributs supplémentaires pour définir chaque nœud de l’arborescence.

### <a name="example"></a>Exemple
 Cet exemple montre deux pages de propriétés, **options** et **mise en retrait**, ainsi qu’un nœud qui contient la deuxième page de propriétés.

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

## <a name="proffer-the-language-service-at-run-time"></a>Offrir le service de langage au moment de l’exécution
 Lorsque votre package de langue est chargé, vous devez indiquer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que votre service de langage est prêt. Pour ce faire, proffering le service. Cette opération est effectuée dans la méthode <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>. En outre, vous devez démarrer un minuteur qui appelle votre service de langage pendant les périodes d’inactivité pour que l’analyse en arrière-plan puisse être effectuée. Ce minuteur inactif est également utilisé pour mettre à jour les propriétés de document si vous avez implémenté tout par le biais de la <xref:Microsoft.VisualStudio.Package.DocumentProperties> classe. Pour prendre en charge un minuteur, votre package doit implémenter l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> interface (seule la <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> méthode doit être entièrement implémentée ; les autres méthodes peuvent retourner des valeurs par défaut).

### <a name="example"></a>Exemple
 Cet exemple illustre une approche classique pour proffering un service et fournir un minuteur inactif.

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
                crinfo[0].grfcadvf          = (uint)_OLECADVF.olecadvfModal |
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
