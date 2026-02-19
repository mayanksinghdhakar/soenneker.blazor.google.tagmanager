# Soenneker Blazor Google Tag Manager 📊

![GitHub release](https://img.shields.io/github/release/mayanksinghdhakar/soenneker.blazor.google.tagmanager.svg?style=flat-square)

Welcome to the **Soenneker Blazor Google Tag Manager** repository! This project provides a seamless interop library for integrating Google Tag Manager with Blazor applications. With this library, you can enhance your web analytics and improve your application's performance.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Examples](#examples)
- [Contributing](#contributing)
- [License](#license)
- [Links](#links)

## Introduction

Google Tag Manager (GTM) is a powerful tool for managing JavaScript and HTML tags used for tracking and analytics on websites. By integrating GTM with Blazor, you can easily manage tags without altering your application’s codebase frequently. This library allows developers to utilize the full capabilities of GTM while enjoying the benefits of Blazor's modern web development framework.

## Features

- **Easy Integration**: Quickly set up Google Tag Manager in your Blazor application.
- **Event Tracking**: Capture user interactions with minimal effort.
- **Tag Management**: Manage and deploy tags without code changes.
- **C# Support**: Utilize C# for your tag management logic.
- **Cross-Platform**: Works on all platforms supported by Blazor.

## Installation

To get started with the Soenneker Blazor Google Tag Manager library, you can install it via NuGet. Run the following command in your project directory:

```bash
dotnet add package Soenneker.Blazor.Google.TagManager
```

For more details on the latest releases, please check the [Releases section](https://github.com/mayanksinghdhakar/soenneker.blazor.google.tagmanager/releases). Download the latest version and execute it to start using the library.

## Usage

To use the library in your Blazor application, follow these steps:

1. **Add the GTM script**: Include the Google Tag Manager script in your `index.html` or `_Host.cshtml` file. Replace `GTM-XXXX` with your GTM container ID.

    ```html
    <script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
    new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
    j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
    'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
    })(window,document,'script','dataLayer','GTM-XXXX');</script>
    ```

2. **Initialize the library**: In your `Startup.cs`, add the service for Google Tag Manager.

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddGtm("GTM-XXXX");
    }
    ```

3. **Use the Tag Manager in your components**: You can now access the Tag Manager features in your Blazor components.

    ```razor
    @inject IGtmService GtmService

    <button @onclick="TrackButtonClick">Click Me</button>

    @code {
        private void TrackButtonClick()
        {
            GtmService.PushEvent("button_click", new { button_name = "Click Me" });
        }
    }
    ```

## Examples

### Basic Event Tracking

You can track events like button clicks, form submissions, and more. Here’s a simple example of tracking a button click:

```razor
<button @onclick="TrackButtonClick">Submit</button>

@code {
    private void TrackButtonClick()
    {
        GtmService.PushEvent("form_submission", new { form_id = "contact_form" });
    }
}
```

### Advanced Tag Management

To manage tags dynamically, you can create a service that handles tag logic based on user actions. This allows you to maintain clean code while still leveraging GTM’s capabilities.

```csharp
public class TagManagementService
{
    private readonly IGtmService _gtmService;

    public TagManagementService(IGtmService gtmService)
    {
        _gtmService = gtmService;
    }

    public void TrackPageView(string pageName)
    {
        _gtmService.PushEvent("page_view", new { page = pageName });
    }
}
```

## Contributing

We welcome contributions to the Soenneker Blazor Google Tag Manager library! Here’s how you can help:

1. **Fork the repository**: Create your own copy of the project.
2. **Make changes**: Implement your features or fixes.
3. **Submit a pull request**: Share your changes with the community.

For more details, please check the [Contributing Guidelines](CONTRIBUTING.md).

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Links

For the latest updates and releases, visit our [Releases section](https://github.com/mayanksinghdhakar/soenneker.blazor.google.tagmanager/releases). Download the latest version and execute it to integrate Google Tag Manager into your Blazor application.

Explore the features and enhance your web analytics with ease!