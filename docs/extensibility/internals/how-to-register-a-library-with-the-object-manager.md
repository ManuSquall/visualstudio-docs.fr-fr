---
title: 'Procédure : inscrire une bibliothèque à l’aide du gestionnaire d’objets | Microsoft Docs'
description: Découvrez comment inscrire une bibliothèque à l’aide du gestionnaire d’objets de Visual Studio afin de pouvoir afficher les symboles dans les outils de navigation, tels que Affichage de classes et l’Explorateur d’objets.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8036a0f4fe073473891805766ea8e3bb941951f8
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761380"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Procédure : inscrire une bibliothèque à l’aide du gestionnaire d’objets
Les outils de navigation de symboles, tels que **affichage de classes**, **Explorateur d’objets**, **Explorateur d’appels** et rechercher les **résultats de symbole**, vous permettent d’afficher des symboles dans votre projet ou dans des composants externes. Les symboles incluent des espaces de noms, des classes, des interfaces, des méthodes et d’autres éléments de langage. Les bibliothèques effectuent le suivi de ces symboles et les exposent au [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gestionnaire d’objets qui remplit les outils avec les données.

 Le gestionnaire d’objets effectue le suivi de toutes les bibliothèques disponibles. Chaque bibliothèque doit s’inscrire auprès du gestionnaire d’objets avant de fournir des symboles pour les outils de navigation de symboles.

 En général, vous inscrivez une bibliothèque lors du chargement d’un VSPackage. Toutefois, cette opération peut être effectuée à un autre moment en fonction des besoins. Vous annulez l’inscription de la bibliothèque lorsque le VSPackage s’arrête.

 Pour inscrire une bibliothèque, utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> méthode. Pour une bibliothèque de code managé, utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> méthode.

 Pour annuler l’inscription d’une bibliothèque, utilisez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> méthode.

 Pour obtenir une référence au gestionnaire d’objets, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> , transmettez l' <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> ID de service à la `GetService` méthode.

## <a name="register-and-unregister-a-library-with-the-object-manager"></a>Inscrire et annuler l’inscription d’une bibliothèque à l’aide du gestionnaire d’objets

### <a name="to-register-a-library-with-the-object-manager"></a>Pour inscrire une bibliothèque à l’aide du gestionnaire d’objets

1. Créer une bibliothèque.

    ```vb
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing
    Private m_nLibraryCookie As UInteger = 0
    ' Create Library.
    m_CallBrowserLibrary = New CallBrowser.Library()
    ```

    ```csharp
    private CallBrowser.Library m_CallBrowserLibrary = null;
    private uint m_nLibraryCookie = 0;
    // Create Library.
    m_CallBrowserLibrary = new CallBrowser.Library();

    ```

2. Obtenez une référence à un objet du <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> type et appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> méthode.

    ```vb
    Private Sub RegisterLibrary()
        If m_nLibraryCookie <> 0 Then
            Throw New Exception("Library already registered with Object Manager")
        End If

        ' Obtain a reference to IVsObjectManager2 type object.
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)
        If objManager Is Nothing Then
            Throw New NullReferenceException("GetService failed for SVsObjectManager")
        End If

        Try
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)
        Catch e As Exception
            ' Code to handle any CLS-compliant exception.
            Trace.WriteLine(e.Message)
            Throw
        End Try
    End Sub
    ```

    ```csharp
    private void RegisterLibrary()
    {
        if (m_nLibraryCookie != 0)
            throw new Exception("Library already registered with Object Manager");

        // Obtain a reference to IVsObjectManager2 type object.
        IVsObjectManager2 objManager =
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;
        if (objManager == null)
            throw new NullReferenceException("GetService failed for SVsObjectManager");

        try
        {
            int hr =
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,
                                                 out m_nLibraryCookie);
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);
        }
        catch (Exception e)
        {
            // Code to handle any CLS-compliant exception.
            Trace.WriteLine(e.Message);
            throw;
        }
    }

    ```

### <a name="to-unregister-a-library-with-the-object-manager"></a>Pour annuler l’inscription d’une bibliothèque à l’aide du gestionnaire d’objets

1. Obtenez une référence à un objet du <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> type et appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> méthode.

    ```vb
    Private Sub UnregisterLibrary()
        If m_nLibraryCookie <> 0 Then
            ' Obtain a reference to IVsObjectManager2 type object.
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)
            If objManager Is Nothing Then
                Throw New NullReferenceException("GetService failed for SVsObjectManager")
            End If

            Try
                objManager.UnregisterLibrary(m_nLibraryCookie)
            Catch e As Exception
                ' Code to handle any CLS-compliant exception.
                Trace.WriteLine(e.Message)
                Throw
            Finally
                m_nLibraryCookie = 0
            End Try
        End If
    End Sub
    ```

    ```csharp
    private void UnregisterLibrary()
    {
        if (m_nLibraryCookie != 0)
        {
            // Obtain a reference to IVsObjectManager2 type object.
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;
            if (objManager == null)
                throw new NullReferenceException("GetService failed for SVsObjectManager");

            try
            {
                objManager.UnregisterLibrary(m_nLibraryCookie);
            }
            catch (Exception e)
            {
                // Code to handle any CLS-compliant exception.
                Trace.WriteLine(e.Message);
                throw;
            }
            finally
            {
                m_nLibraryCookie = 0;
            }
        }
    }

    ```

## <a name="see-also"></a>Voir aussi
- [Extensibilité du service de langage hérité](../../extensibility/internals/legacy-language-service-extensibility.md)
- [Prise en charge des outils de navigation de symboles](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Comment : exposer des listes de symboles fournies par la bibliothèque au gestionnaire d’objets](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
