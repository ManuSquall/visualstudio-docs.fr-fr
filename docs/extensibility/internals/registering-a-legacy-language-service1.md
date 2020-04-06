---
title: Enregistrement d’un service de langue héritée1 Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91776382fff1818986049558c9d86e8fce4d0dd7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705902"
---
# <a name="registering-a-legacy-language-service"></a>Inscription d’un service de langage hérité
Dans le cadre de forfait géré (MPF), le service linguistique est offert par un VSPackage (voir [VSPackages](../../extensibility/internals/vspackages.md)) et est enregistré avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’ajout de clés de registre et d’entrées. Ce processus d’enregistrement se fait en partie pendant l’installation et en partie au moment de l’exécution.

## <a name="register-the-language-service-by-using-attributes"></a>Enregistrez le service linguistique en utilisant des attributs
 Les attributs suivants sont utilisés pour enregistrer un service linguistique.

- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>

  Ces attributs sont expliqués ci-dessous

### <a name="provideserviceattribute"></a>FournirServiceAttribute
 Cet attribut enregistre votre service linguistique en tant que service.

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

### <a name="providelanguageserviceattribute"></a>FournirLanguageServiceAttribute
 Cet attribut enregistre votre service linguistique spécifiquement en tant que service linguistique. Il vous permet de définir des options qui spécifient les fonctionnalités que votre service linguistique offre. L’exemple montre un sous-ensemble des options qu’un service linguistique peut fournir. Pour l’ensemble des options <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>de service linguistique, voir .

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
 Cet attribut associe votre service linguistique à une extension de fichiers. Chaque fois qu’un fichier avec cette extension est chargé, dans n’importe quel projet, votre service linguistique est démarré et utilisé pour afficher le contenu du fichier.

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
 Cet attribut enregistre un emplacement à partir duquel des modèles d’extension ou d’extrait de code sont obtenus. Ces informations sont utilisées par le **Code Snippets Browser** et par l’éditeur lorsqu’un extrait de code est inséré dans le fichier source.

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
 Cet attribut enregistre une page de propriété à afficher dans la boîte de dialogue **Options** dans la catégorie **Text Editor.** Utilisez l’un de ces attributs pour que chaque page soit affichée pour votre service linguistique. Si vous avez besoin d’organiser vos pages dans une structure d’arbre, utilisez des attributs supplémentaires pour définir chaque nœud de l’arbre.

### <a name="example"></a>Exemple
 Cet exemple montre deux pages de propriété, **Options** et **Indenting**, et un nœud qui contient la deuxième page de propriété.

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

## <a name="proffer-the-language-service-at-run-time"></a>Offrir le service linguistique à l’heure de l’exécution
 Lorsque votre forfait linguistique est [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chargé, vous devez dire que votre service linguistique est prêt. Vous le faites en offrant le service. Cela se fait <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> dans la méthode. En outre, vous devez démarrer une minuterie qui appelle votre service linguistique pendant les périodes de marche au ralenti afin que l’analyse de fond puisse être accomplie. Cette minuterie au ralenti est également utilisée pour mettre <xref:Microsoft.VisualStudio.Package.DocumentProperties> à jour les propriétés des documents si vous en avez implémenté tout au long de la classe. Afin de prendre en charge une minuterie, votre package doit implémenter l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> (seule la <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> méthode doit être entièrement mise en œuvre; les méthodes restantes peuvent retourner les valeurs par défaut).

### <a name="example"></a>Exemple
 Cet exemple montre une approche typique pour offrir un service et fournir une minuterie inactive.

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
