package com.example.demo;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.http.HttpStatus;
import org.springframework.web.bind.annotation.ExceptionHandler;
import org.springframework.web.bind.annotation.ResponseStatus;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class CalculatorController {

    private final CalculatorService calculatorService;

    public CalculatorController(CalculatorService calculatorService) {
        this.calculatorService = calculatorService;
    }

    @ExceptionHandler(IllegalArgumentException.class)
    @ResponseStatus(HttpStatus.BAD_REQUEST)
    public String handleBadInput(IllegalArgumentException exception) {
        return exception.getMessage();
    }

    @GetMapping("/api/calculate")
    public int calculate(@RequestParam int a,
                         @RequestParam int b,
                         @RequestParam String operation) {
        return switch (operation) {
            case "add" -> calculatorService.add(a, b);
            case "subtract" -> calculatorService.subtract(a, b);
            case "multiply" -> calculatorService.multiply(a, b);
            case "divide" -> calculatorService.divide(a, b);
            default -> 0;
        };
    }
}

