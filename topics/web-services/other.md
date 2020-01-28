# Other topics

## LocaleResolver and ResourceBundleMessageSource

Just create a default "message.properties" file, then an international "message_es.properties", 
and then add the following beans into SpringBoot's Application class:

´´´java

    @Bean
    public LocaleResolver localeResolver() {
        SessionLocaleResolver localeResolver = new SessionLocaleResolver();
        localeResolver.setDefaultLocale(Locale.US);
        return localeResolver;
    }

    @Bean
    public ResourceBundleMessageSource bundleMessageSource() {
        ResourceBundleMessageSource messageSource = new ResourceBundleMessageSource();
        messageSource.setBasename("messages");
        return messageSource;
    }

´´´

And then in a @RestController Class:

´´´
@RestController
public class HelloWorldController {

    @Autowired
    private MessageSource messageSource;

    @GetMapping(path = "/hello-world-international")
    public String helloWorldInternationalized() {

        return messageSource.getMessage("good.morning.message", null, LocaleContextHolder.getLocale());
    }
´´´



