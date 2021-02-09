---
title: 'Comment : générer des informations de Registre pour un programme d’installation | Microsoft Docs'
description: Découvrez comment utiliser l’utilitaire RegPkg.exe dans Visual Studio pour générer des informations de Registre VSPackage pour l’incorporation dans un package d’installation Windows Installer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
- VSPackages, registration manifests
ms.assetid: b1b41012-a777-4ccf-81a6-3b41f0e96583
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a32d8f57be2e1e4c8a2855f7f9008eaed2ae4eac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874059"
---
# <a name="how-to-generate-registry-information-for-an-installer"></a>Comment : générer des informations de Registre pour un programme d’installation

L’utilitaire *RegPkg.exe* peut être utilisé pour générer un manifeste d’inscription pour un VSPackage managé. Le manifeste peut être incorporé dans un package d’installation Windows Installer. RegPkg peut également générer un fichier qui peut être inclus dans un fichier source d’installation basé sur le [Windows Installer ensemble d’outils XML](https://wixtoolset.org/).

> [!IMPORTANT]
> RegPkg génère des noms de chemin d’accès spécifiques à votre système de développement. par conséquent, chaque fois que vous utilisez RegPkg, vous devez modifier la sortie pour utiliser les propriétés mises en forme appropriées Windows Installer. Par exemple, la `InprocServer32` valeur doit être *\<SystemFolder\>mscoree.dll* et les chemins d’accès doivent utiliser *\<#filekey\>* et *\<$componentkey\>* . L’ajustement de la sortie de cette manière prend en charge les ordinateurs sur lesquels Windows est installé sur un autre lecteur ou dans un répertoire différent, les noms de répertoire localisés et les chemins que les utilisateurs peuvent choisir. Pour plus d’informations, consultez [mise en forme](https://msdn.microsoft.com/library?url=/library/msi/setup/formatted.asp) dans le kit de développement logiciel (SDK) Windows Installer. Si vous suivez les conventions RegPkg pour vos chemins d’accès système de développement (par exemple, les ID de fichier de la forme *File_ \<filename\>*), vous devez effectuer moins de modifications.

## <a name="to-create-a-registration-manifest"></a>Pour créer un manifeste d’inscription

- Exécutez RegPkg avec le commutateur **/regfile** . Fournissez d’autres commutateurs, le nom du fichier de sortie et le chemin d’accès du VSPackage.

     Par exemple, à l’invite de commandes, tapez ce qui suit :

    ```
    <Visual Studio SDK installation path>\VisualStudioIntegration\Tools\Bin\RegPkg /regfile:MyRegFile.reg MyPackage.dll
    ```

## <a name="to-view-a-registration-manifest"></a>Pour afficher un manifeste d’inscription

- Ouvrez le manifeste d’inscription dans n’importe quel éditeur de texte.

     L’exemple suivant est le manifeste d’inscription créé par RegPkg pour le service de langage IronPython :

    ```
    REGEDIT4

    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages]
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions]
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python]
    @="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}"
    "DisplayName"="131"
    "IndexPath"="C:\\VSSDK80\\2006.07\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\bin\\Release\\CodeSnippets\\SnippetsIndex.xml"
    "LangStringId"="python"
    "Package"="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}"
    "ShowRoots"=dword:00000000
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python\ForceCreateDirs]
    "Python"="C:\\VSSDK80\\2006.07\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\bin\\Release\\CodeSnippets\\Snippets\\;%MyDocs%\Code Snippets\Python\My Code Snippets\"
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python\Paths]
    "Python"="C:\\VSSDK80\\2006.07\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\bin\\Release\\CodeSnippets\\Snippets\\;%MyDocs%\Code Snippets\Python\My Code Snippets\"
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Packages]
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Packages\{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}]
    @="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonPackage, IronPython.LanguageService, Version=1.0.2373.36479, Culture=neutral, PublicKeyToken=null"
    "InprocServer32"="C:\\WINNT\\system32\\mscoree.dll"
    "Class"="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonPackage"
    "Assembly"="IronPython.LanguageService, Version=1.0.2373.36479, Culture=neutral, PublicKeyToken=null"
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages]
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\File Extensions]
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\File Extensions\.py]
    @="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}"
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages]
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\Language Services]
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Languages\Language Services\Python]
    @="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}"
    "Package"="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}"
    "LangResID"=dword:00000064
    "ShowMatchingBrace"=dword:00000001
    "CodeSense"=dword:00000001
    "MatchBraces"=dword:00000001
    "EnableCommenting"=dword:00000001
    "ShowCompletion"=dword:00000001
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Packages]
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Packages\{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}]
    "ID"=dword:00000001
    "MinEdition"="standard"
    "ProductVersion"="1.0"
    "ProductName"="Visual Studio Integration of IronPython Language Service"
    "CompanyName"="Microsoft Corporation"
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Services]
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Services\{923b4811-26e4-4347-ac8a-244762798e1c}]
    @="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}"
    "Name"="IPythonLibraryManager"
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Services]
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Services\{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}]
    @="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}"
    "Name"="Python"

    ```

## <a name="to-create-a-windows-installer-xml-toolset-include-file"></a>Pour créer un fichier d’ensemble d’outils XML Windows Installer

- Exécutez RegPkg avec le commutateur **/wixfile** Fournissez d’autres commutateurs, le nom du fichier de sortie et le chemin d’accès du VSPackage.

     Par exemple, à l’invite de commandes, tapez ce qui suit :

    ```
    <Visual Studio SDK installation path>\VisualStudioIntegration\Tools\Bin\RegPkg /codebase /wixfile:IronPython.LanguageService.wxi ..\bin\Release\IronPython.LanguageService.dll
    ```

## <a name="to-view-a-windows-installer-xml-toolset-include-file"></a>Pour afficher un fichier d’ensemble d’outils XML Windows Installer

- Ouvrez le fichier include de l’ensemble d’outils XML Windows Installer dans n’importe quel éditeur de texte.

     L’exemple suivant est le fichier include créé par RegPkg pour le service de langage IronPython :

    ```xml
    <Include>

      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\IntellisenseProviders\IronPythonCodeProvider">
        <Registry Name="GUID" Value="{9c1807ea-d222-4775-afa8-c092c580e451}" Type="string" />
        <Registry Name="AddItemLanguageName" Value="Iron Python" Type="string" />
        <Registry Name="DefaultExtension" Value=".py" Type="string" />
        <Registry Name="ShortLanguageName" Value="IronPython;Python" Type="string" />
        <Registry Name="TemplateFolderName" Value="IronPython" Type="string" />
      </Registry>

      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python" Value="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}" Type="string">
        <Registry Name="DisplayName" Value="131" Type="string" />
        <Registry Name="IndexPath" Value="C:\\VSSDK80\\2006.08\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\Setup\\[$ComponentPath]\\CodeSnippets\\SnippetsIndex.xml" Type="string" />
        <Registry Name="LangStringId" Value="python" Type="string" />
        <Registry Name="Package" Value="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}" Type="string" />
        <Registry Name="ShowRoots" Value="0" Type="integer" />
      </Registry>

      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python\ForceCreateDirs">
        <Registry Name="Python" Value="C:\\VSSDK80\\2006.08\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\Setup\\[$ComponentPath]\\CodeSnippets\\Snippets\\;%MyDocs%\Code Snippets\Python\My Code Snippets\" Type="string" />
      </Registry>

      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\CodeExpansions\Python\Paths">
        <Registry Name="Python" Value="C:\\VSSDK80\\2006.08\\VisualStudioIntegration\\Samples\\IronPythonIntegration\\Setup\\[$ComponentPath]\\CodeSnippets\\Snippets\\;%MyDocs%\Code Snippets\Python\My Code Snippets\" Type="string" />
      </Registry>

      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\File Extensions\.py" Value="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}" Type="string" />

      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Languages\Language Services\Python" Value="{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}" Type="string">
        <Registry Name="Package" Value="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}" Type="string" />
        <Registry Name="LangResID" Value="100" Type="integer" />
        <Registry Name="ShowCompletion" Value="1" Type="integer" />
        <Registry Name="ShowMatchingBrace" Value="1" Type="integer" />
        <Registry Name="CodeSense" Value="1" Type="integer" />
        <Registry Name="MatchBraces" Value="1" Type="integer" />
        <Registry Name="EnableCommenting" Value="1" Type="integer" />
        <Registry Name="DefaultToInsertSpaces" Value="1" Type="integer" />
      </Registry>

      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Packages\{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}" Value="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonPackage, IronPython.LanguageService, Version=1.0.2394.27719, Culture=neutral, PublicKeyToken=null" Type="string">
        <Registry Name="InprocServer32" Value="[SystemFolder]mscoree.dll" Type="string" />
        <Registry Name="Class" Value="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonPackage" Type="string" />
        <Registry Name="CodeBase" Value="[#File_IronPython.LanguageService.dll]" Type="string" />
        <Registry Name="ID" Value="1" Type="integer" />
        <Registry Name="MinEdition" Value="standard" Type="string" />
        <Registry Name="ProductVersion" Value="1.0" Type="string" />
        <Registry Name="ProductName" Value="Visual Studio Integration of IronPython Language Service" Type="string" />
        <Registry Name="CompanyName" Value="Microsoft Corporation" Type="string" />
      </Registry>

      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\CLSID\{9c1807ea-d222-4775-afa8-c092c580e451}" Value="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonIntellisenseProvider" Type="string">
        <Registry Name="InprocServer32" Value="[SystemFolder]mscoree.dll" Type="string" />
        <Registry Name="Class" Value="Microsoft.Samples.VisualStudio.IronPythonLanguageService.PythonIntellisenseProvider" Type="string" />
        <Registry Name="CodeBase" Value="[#File_IronPython.LanguageService.dll]" Type="string" />
        <Registry Name="ThreadingModel" Value="Both" Type="string" />
      </Registry>

      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Services\{923b4811-26e4-4347-ac8a-244762798e1c}" Value="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}" Type="string">
        <Registry Name="Name" Value="IPythonLibraryManager" Type="string" />
      </Registry>

      <Registry Root="HKLM" Key="Software\Microsoft\VisualStudio\8.0\Services\{ae8ce01a-b3ff-4c19-8c80-54669c197f2c}" Value="{1b05e2b4-7c21-4f63-910e-29fe55eb5f8b}" Type="string">
        <Registry Name="Name" Value="Python" Type="string" />
      </Registry>
    </Include>
    ```

## <a name="see-also"></a>Voir aussi

- [Inscrire des VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)
- [VSPackages](../../extensibility/internals/vspackages.md)
