# angular-vars-access

@RestController
public class ConfigController {

    @Value("${custom.config}")
    private String customConfig;

    @GetMapping("/api/config")
    public ResponseEntity<Map<String, String>> getConfig() {
        Map<String, String> config = new HashMap<>();
        config.put("customConfig", customConfig);
        return ResponseEntity.ok(config);
    }
}
