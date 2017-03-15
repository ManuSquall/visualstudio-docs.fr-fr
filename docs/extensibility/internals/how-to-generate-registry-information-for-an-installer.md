---
title: "Comment : g&#233;n&#233;rer des informations de Registre pour un programme d&#39;installation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "inscription, les packages VS"
  - "Packages VS, l'inscription"
  - "VSPackages, les manifestes de l'inscription"
ms.assetid: b1b41012-a777-4ccf-81a6-3b41f0e96583
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# Comment : g&#233;n&#233;rer des informations de Registre pour un programme d&#39;installation
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

l'utilitaire de RegPkg.exe peut être utilisé pour générer un manifeste d'alignement pour un VSPackage managé.  Le manifeste peut être incorporé à un package d'installation Windows Installer.  RegPkg peut également générer un fichier qui peut être inclus dans un fichier source d'installation sur [Windows Installer XML Toolset](http://go.microsoft.com/fwlink/?LinkId=62238).  
  
> [!IMPORTANT]
>  RegPkg génère des noms de chemin d'accès spécifiques à votre système de développement, ce qui fait que chaque fois que vous utilisez RegPkg, vous devez modifier la sortie pour utiliser les propriétés mises en forme par Windows Installer appropriées.  Par exemple, la valeur InprocServer32 doit être **\[SystemFolder\]mscoree.dll** et les chemins d'accès doivent utiliser **\[\#filekey\]** et **\[$componentkey\]**.  Ajuster la sortie prend en charge de cette façon des ordinateurs avec windows installées sur un lecteur différent ou dans un répertoire différent, les noms de répertoire localisés, et les chemins que les utilisateurs peuvent sélectionner.  Pour plus d'informations, consultez [Formatted](http://go.microsoft.com/fwlink/?LinkId=71120) dans le Kit de développement Windows Installer.  Si vous suivez des conventions de RegPkg pour votre système de développement chemin d'accès\-pour l'exemple, les identificateurs de fichier du formulaire File\_*nom de fichier*\- vous avez besoin apportez moins modifications.  
  
### pour créer un manifeste d'alignement  
  
-   exécutez RegPkg avec le commutateur d' **\/regfile** .  fournissez tous les autres commutateurs, le nom du fichier de sortie, et le chemin d'accès du VSPackage.  
  
     Par exemple, à l'invite de commandes de, tapez semblable à la suivante :  
  
    ```  
    [Visual Studio SDK installation path]\VisualStudioIntegration\Tools\Bin\RegPkg /regfile:MyRegFile.reg MyPackage.dll  
    ```  
  
### pour afficher un manifeste d'alignement  
  
-   Ouvrez le manifeste d'inscription dans un éditeur de texte.  
  
     L'exemple suivant est le manifeste d'alignement que RegPkg crée pour le service de langage IronPython :  
  
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
  
### Pour créer un fichier Include d'ensemble d'outils XML de Windows Installer  
  
-   exécutez RegPkg avec le commutateur d' **\/wixfile** .  fournissez tous les autres commutateurs, le nom du fichier de sortie, et le chemin d'accès du VSPackage.  
  
     Par exemple, à l'invite de commandes de, tapez semblable à la suivante :  
  
    ```  
    [Visual Studio SDK installation path]\VisualStudioIntegration\Tools\Bin\RegPkg /codebase /wixfile:IronPython.LanguageService.wxi ..\bin\Release\IronPython.LanguageService.dll  
    ```  
  
### Pour afficher un fichier Include d'ensemble d'outils XML de Windows Installer  
  
-   Ouvrez le fichier Include d'ensemble d'outils XML de Windows Installer dans un éditeur de texte.  
  
     L'exemple suivant est le fichier Include que RegPkg crée pour le service de langage IronPython :  
  
    ```  
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
  
## Voir aussi  
 [Registering VSPackages](http://msdn.microsoft.com/fr-fr/31e6050f-1457-4849-944a-a3c36b76f3dd)   
 [Packages VS](../../extensibility/internals/vspackages.md)