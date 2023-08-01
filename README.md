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

@Injectable()
export class ConfigService {

  private config: any;

  constructor(private http: HttpClient) { }

  loadConfig() {
    return this.http.get('/api/config').toPromise().then(config => {
      this.config = config;
    });
  }

  getConfig() {
    return this.config;
  }
}


