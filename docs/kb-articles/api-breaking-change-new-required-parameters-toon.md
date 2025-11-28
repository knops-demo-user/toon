# API Breaking Change: New Required Parameters - toon

# API Breaking Change: New Required Parameters

> **Problem Statement:** Users may encounter 422 validation errors due to recently introduced required parameters in the API.

---

## Applies To

- **Product/Repository:** toon
- **Language/Framework:** None
- **Versions:** All versions
- **Environment:** Development/Production/Both

---

## Symptoms

Users experiencing this issue may observe:

- **Error Messages:**
  ```
  422 Unprocessable Entity: Required parameters are missing.
  ```

- **Behavior:**
  - Users attempting to utilize the CLI API with stdin input may receive validation errors despite correctly formed requests.
  - Specific parameters necessary for successful API calls may not be specified, leading to failures.

- **Impact:**
  - Workflows relying on the API are disrupted, causing delays in operations that depend on the updated functionality.

---

## Root Cause

### Technical Explanation

The introduction of new required parameters for stdin input handling has led to 422 validation errors for users attempting to make API calls without providing the necessary information. 

**Key factors:**
- The recent change in the API where specific parameters are now mandatory.
- Modifications in how stdin input is processed, necessitating additional parameters to be included in requests.
- Lack of backward compatibility for previous API interactions that did not require these parameters.

---

## Resolution

### Migration Guide (For Code-Level Changes)

**IMPORTANT:** If this issue is due to code changes (API updates, config changes, breaking changes), provide a migration guide:

#### Before (Old Code/Config):
```json
{
  "input": "some input data"
  // Previously, no additional parameters were required
}
```

#### After (New Code/Config):
```json
{
  "input": "some input data",
  "requiredParamA": "value for A",
  "requiredParamB": "value for B"
}
```

#### What Changed:
- `requiredParamA` is now required for stdin input processing.
- `requiredParamB` is also newly required, affecting the API response.
- Legacy API calls without these parameters will lead to validation errors.

---

### Step-by-Step Fix

**Method 1: Updating API Calls**

Follow these steps to resolve the issue:

1. **Identify Required Parameters**
   - Ensure that any API requests utilize the new parameters.
   - Check documentation or release notes for additional context on parameter requirements.
   
2. **Modify API Requests**
   - Update your API call to include the mandatory parameters as specified above.
   - Verify your payload is correctly formatted with all required fields.

3. **Test Your API Call**
   ```bash
   curl -X POST \
     -H "Content-Type: application/json" \
     -d '{"input": "some input data", "requiredParamA": "value for A", "requiredParamB": "value for B"}' \
     http://api.example.com/your-endpoint
   ```

**Expected Result:**
The API should return a successful response (e.g., 200 OK), indicating that all required parameters have been appropriately included.

**Verification:**
```bash
curl -X GET http://api.example.com/your-endpoint?input=test 
# Ensure the correct response is received.
```

---

**Method 2: Fallback to Previous Version** *(If primary method not feasible)*

If updating API calls is not feasible for the time being:

1. Roll back to the previous, stable version of your application that did not include these new required parameters.
2. Ensure that the environment is stable before updates.

---

## Workarounds

If the above fix cannot be applied immediately:

**Temporary Solution:**
- Use previous versions of your API until you can update requests.
- Notify users of the temporary nature of this workaround and advise on the forthcoming changes.

**Note:** This is a temporary measure. Apply the full resolution when possible.

---

## Prevention & Best Practices

To avoid this issue in the future:

1. **Stay Updated on API Changes**
   - Regularly monitor release notes and documentation for new API versions.
   - Subscribe to updates via your project repository.

2. **Validate API Requests**
   - Implement client-side validations for required fields before sending requests.
   - Incorporate error handling for validation responses.

3. **Versioning of API**
   - Use versioning in your API to mitigate the impact of breaking changes. Consider allowing requests against older versions if feasible.

---

## References

- **Related GitHub Issues:** #107
- **Pull Requests:** #111, #110
- **Documentation:** [API Documentation](link-to-docs)
- **Related Articles:** [Link to related configuration guides]

---

## Related Articles

- [Troubleshooting API Validation Errors]
- [Configuration Best Practices for API Integrations]

---

## Support Escalation

If this article does not resolve your issue:

1. **Gather the following information:**
   - Full error message and stack trace
   - Environment details (OS, versions, configurations)
   - Steps to reproduce the issue
   - Logs from: API service logs

2. **Contact Support:**
   - Submit via: [Support channel]
   - Include: All information from step 1
   - Reference: This KB article

---

*Last Updated: October 23, 2023*
*Article ID: 24609*